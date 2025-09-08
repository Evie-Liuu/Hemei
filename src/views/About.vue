<template>
  <div class="page-background">
    <div v-if="isLoading" class="loading-overlay">
      <div class="loading-text">
        <span style="--i: 1">載</span>
        <span style="--i: 2">入</span>
        <span style="--i: 3">中</span>
        <span style="--i: 4">.</span>
        <span style="--i: 5">.</span>
        <span style="--i: 6">.</span>
      </div>
    </div>
    <div class="w-screen h-screen bg-rice-500">
      <main class="w-full h-full flex justify-center">
        <iframe
          @load="onIframeLoad"
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
  </div>
</template>
<script setup>
import { ref } from "vue";

const isLoading = ref(true);

const onIframeLoad = () => {
  isLoading.value = false;
};
</script>
<style scoped>
</style>