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
    <main
      class="w-screen h-screen flex justify-center items-center bg-[url('@/assets/images/var02/Mobile_BackColor_N.png')] bg-cover bg-center overflow-hidden lg:bg-[url('@/assets/images/var02/BackColor_N.png')]"
    >
      <div
        class="relative w-full h-2/3 lg:w-320 lg:h-180 mx-auto translate-y-0 lg:translate-y-13"
      >
        <iframe
          @load="onIframeLoad"
          src="https://www.thinglink.com/view/scene/2019642406927860198"
          type="text/html"
          class="w-full h-full"
          webkitallowfullscreen
          mozallowfullscreen
          allowfullscreen
          scrolling="no"
        ></iframe>
        <div
          class="absolute inset-0 lg:border-10 border-pblue-100 pointer-events-none"
        ></div>
      </div>
    </main>
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