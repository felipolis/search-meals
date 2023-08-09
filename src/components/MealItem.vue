<template>
  <div
    class="bg-white shadow rounded-xl"
  >
    <router-link :to="{ name: 'mealDetails', params: { id: meal.idMeal } }">
      <img
        :src="meal.strMealThumb"
        :alt="meal.strMeal"
        class="rounded-t-xl h-48 w-full object-cover"
      />
    </router-link>
    <div class="p-3">
      <h3 class="font-bold">{{ meal.strMeal }}</h3>
      <p class="mb-4">
        Lorem ipsum dolor sit amet consectetur adipisicing elit. Minus deleniti,
        vitae dolorem mollitia ea impedit, molestias officiis aspernatur rerum
        earum quis culpa est. Ab dolorem rem perspiciatis numquam. Nulla,
        commodi?
      </p>
      <div class="flex items-center justify-between">
        <YoutubeButton :href="meal.strYoutube"> Youtube </YoutubeButton>
      </div>
    </div>
  </div>
</template>

<script setup>

import { defineProps } from "vue";
import YoutubeButton from "../components/YoutubeButton.vue";

const { meal } = defineProps({
    meal: {
        type: Object,
        required: true
    }
});

</script>
