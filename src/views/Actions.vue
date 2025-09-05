<template>
  <div class="actions-wrapper">
    <!-- Left decorative clouds -->
    <div class="cloud-container-left">
      <img
        v-for="cloud in leftClouds"
        :key="cloud.id"
        :src="cloud.src"
        :style="cloud.style"
        alt="Decorative Cloud"
      />
    </div>
    <!-- Right decorative clouds -->
    <div class="cloud-container-right">
      <img
        v-for="cloud in rightClouds"
        :key="cloud.id"
        :src="cloud.src"
        :style="cloud.style"
        alt="Decorative Cloud"
      />
    </div>

    <header class="relative z-5 pt-25 w-full shadow-md bg-header text-rice-500">
      <div class="container mx-auto flex items-center p-4">
        <div class="w-1/3">
          <router-link to="/" class="back-home-btn">
            <span class="text">回首頁</span>
            <span class="icon">←</span>
          </router-link>
        </div>
        <div class="w-1/3 text-center">
          <h1 class="text-2xl md:text-3xl font-bold">行動追蹤</h1>
        </div>
        <div class="w-1/3"></div>
      </div>
    </header>
    <main
      class="p-10 flex flex-col justify-center items-center gap-8 max-w-7xl md:mx-auto"
    ></main>
  </div>
</template>
<script setup>
import { ref, computed, onMounted } from "vue";

// Import tree images
import cloud1 from "@/assets/images/Tree_1.png";

// const cloudImages = [cloud1, ];
const leftClouds = ref([]);
const rightClouds = ref([]);

const generateClouds = (count) => {
  const trees = [];
  for (let i = 0; i < count; i++) {
    // const randomTreeIndex = Math.floor(Math.random() * treeImages.length);
    trees.push({
      id: `tree-${i}`,
      // src: treeImages[randomTreeIndex],
      src: cloud1,
      style: {
        top: `${i * 150 + Math.random() * 30}px`, // Overlap by setting step less than image height
        transform: `rotate(${(Math.random() - 0.5) * 15}deg) scaleX(${
          Math.random() > 0.5 ? 1 : -1
        })`,
        left: `${(Math.random() - 0.5) * 60}px`, // Horizontal jitter
        zIndex: i,
      },
    });
  }
  return trees;
};

onMounted(() => {
  leftClouds.value = generateClouds(10);
  rightClouds.value = generateClouds(10);
});
</script>
<style scoped>
.actions-wrapper {
  position: relative;
  overflow-x: hidden;
  overflow-y: hidden;
}

.cloud-container-left,
.cloud-container-right {
  position: absolute;
  top: 140px;
  bottom: 0;
  width: 220px; /* Adjust width to contain clouds */
  pointer-events: none;
  z-index: 0;
}

.cloud-container-left {
  left: -55px;
}

.cloud-container-right {
  right: -55px;
}

.cloud-container-left img,
.cloud-container-right img {
  position: absolute;
  width: 200px;
  height: auto;
}

/* RWD: 在小螢幕上隱藏裝飾圖片 */
@media (max-width: 1480px) {
  .cloud-container-left,
  .cloud-container-right {
    display: none;
  }
}
</style>