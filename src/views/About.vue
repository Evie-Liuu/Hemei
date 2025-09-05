<template>
  <div v-if="isLoading" class="loading-overlay">
    <img src="" class="loader" alt="Loading..." />
    <p>載入中...</p>
  </div>
  <div class="w-screen h-screen bg-rice-500">
    <main class="w-full h-full flex justify-center">
      <iframe
        src="https://www.thinglink.com/view/scene/2016738261199749797"
        type="text/html"
        class="w-full h-full pt-20"
        style="border: none"
        webkitallowfullscreen
        mozallowfullscreen
        allowfullscreen
        scrolling="no"
      ></iframe>
    </main>
  </div>
</template>
<script setup>
import { ref, onMounted } from "vue";

const isLoading = ref(true);

onMounted(() => {
  setTimeout(() => {
    isLoading.value = false;
  }, 2000);
});
</script>
<style scoped>
</style>