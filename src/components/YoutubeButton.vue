<template>
  <a
    :href="href"
    target="_blank"
    class="px-3 py-2 text-white rounded border-2 border-red-600 bg-red-500 hover:bg-red-600 transition-colors"
    >Youtube</a
  >
</template>

<script setup>
    import { defineProps } from "vue";

    const props = defineProps({
        href: String
    });
</script>
