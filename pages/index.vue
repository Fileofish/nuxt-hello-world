<template>
  <h1>{{ title }}</h1>
</template>

<script setup>
import { useAsyncData } from 'nuxt/app';
import { useRoute } from 'vue-router';
import { ref } from 'vue';

const route = useRoute();
const title = ref('Загрузка...');

useAsyncData('titleData', async () => {
  const queryTitle = route.query.title;
  if (queryTitle) {
    title.value = queryTitle;
  } else {
    title.value = 'Заголовок по умолчанию';
  }
});
</script>
