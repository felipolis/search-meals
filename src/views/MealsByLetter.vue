<template>
    <div class="flex justify-center gap-2 mt-2">
      <router-link
        v-for="letter in letters"
        :key="letter"
        :to="{name: 'byLetter', params: {letter}}"
      >
        {{ letter }}
      </router-link>
    </div>

    <div class="grid grid-cols-1 md:grid-cols-3 gap-5 p-8">
    <MealItem v-for="meal in meals" :key="meal.idMeal" :meal="meal" />
  </div>
  </template>
  
<script setup>
import { computed } from '@vue/reactivity'
import { onMounted, watch } from 'vue';
import { useRoute } from 'vue-router';
import store from '../store';
import MealItem from "../components/MealItem.vue";

const letters = "ABCDEFGHIJKLMNOPQRSTUVWXYZ".split("");
const meals = computed(() => store.state.mealsByLetter)
const route = useRoute()

watch(route, () => {
  store.dispatch('searchMealsByLetter', route.params.letter)
})

onMounted(() => {
  store.dispatch('searchMealsByLetter', route.params.letter)
})

</script>
  