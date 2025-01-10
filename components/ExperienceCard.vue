<template>
  <div class="bg-white shadow-md rounded-lg p-6">
    <img :src="image" :alt="title" class="h-48 mx-auto my-5 transform transition duration-300 hover:scale-110" />
    <h3 class="text-xl font-semibold text-gray-700 mb-2">{{ title }}</h3>
    <p class="text-gray-500 mb-4">{{ company }} | {{ period }}</p>
    <p class="text-gray-600 text-sm md:text-lg">{{ description }}</p>
  </div>
</template>

<script setup>
defineProps({
  title: String,
  description: String,
  company: String,
  period: String,
  image: String,
})
</script>
