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

    <Meals :meals="meals" />
  </template>
  
<script setup>
import { computed } from '@vue/reactivity'
import { onMounted, watch } from 'vue';
import { useRoute } from 'vue-router';
import store from '../store';
import MealItem from "../components/MealItem.vue";
import Meals from "../components/Meals.vue";

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
  