<template>
  <div class="border border-gray-300 rounded-lg shadow-md p-4 flex flex-col h-full">
    <img :src="image" :alt="title" class="rounded-t-lg w-full h-64 object-cover object-[top_center]" />
    <h3 class="text-lg font-bold mt-2">{{ title }}</h3>
    <p class="text-gray-600 flex-grow text-sm md:text-lg">{{ description }}</p>
    <a :href="link" class="text-primary hover:underline mt-2 inline-block self-start">Acessar Projeto</a>
  </div>
</template>

<script setup>
defineProps({
  title: String,
  description: String,
  image: String,
  link: String,
});
</script>
