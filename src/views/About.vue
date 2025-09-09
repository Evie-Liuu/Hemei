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
    <div
      class="w-screen h-screen bg-rice-500 bg-[url('@/assets/images/var02/BackColor_N.png')]"
    >
      <main class="w-full h-full flex justify-center items-center">
        <iframe
          @load="onIframeLoad"
          src="https://www.thinglink.com/view/scene/2019642406927860198"
          type="text/html"
          class="w-full h-full lg:w-[62%] lg:h-[71%] mt-12 lg:border-10 border-lightblue"
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