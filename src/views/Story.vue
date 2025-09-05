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
          <router-link to="/sdgs" class="back-home-btn">
            <span class="text">回上頁</span>
            <span class="icon">←</span>
          </router-link>
        </div>
        <div class="w-1/3 text-center">
          <h1 class="text-2xl md:text-3xl font-bold">故事牆</h1>
        </div>
        <div class="w-1/3"></div>
      </div>
    </header>
    <main
      class="p-10 flex flex-col justify-center items-center gap-8 max-w-7xl md:mx-auto"
    >
      <HeaderFilter
        @update:filteredInfos="updateFilteredInfos"
        class="flex flex-wrap justify-center items-center gap-4"
      ></HeaderFilter>
      <section
        class="grid grid-cols-1 md:grid-cols-3 gap-5 p-4 md:p-0 md:gap-5"
      >
        <div
          class="animate-fade-in-up cursor-pointer w-80 md:mx-auto min-h-80 bg-white rounded-xl shadow-md overflow-hidden flex flex-col gap-5 hover:scale-105"
          v-for="info in filteredInfos"
          :key="info.id"
          @click="goToStory(info.id)"
        >
          <img
            src="@/assets/images/cover.png"
            alt="Card Image"
            class="h-45 object-cover"
          />
          <div class="p-4 flex flex-col justify-center">
            <h2 class="text-xl font-bold mb-2">{{ info.title }}</h2>
            <p class="text-gray-600 text-sm">{{ info.intro }}</p>
            <p class="text-gray-600 text-sm text-right pe-3">更多</p>
          </div>
        </div>
      </section>
      <div
        v-if="filteredInfos.length === 0"
        class="text-center text-gray-500 mt-8"
      >
        <p>找不到符合條件的故事。</p>
      </div>
    </main>
  </div>
</template>
<script setup>
import { ref, computed, onMounted } from "vue";
import { useRouter } from "vue-router";
import infosData from "@/data/Hemei_story.json";
import typeTags from "@/data/SDGs_goal.json";
import HeaderFilter from "@/components/HeaderFilter.vue";

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

const filteredInfos = ref(infosData);
const updateFilteredInfos = (data) => {
  filteredInfos.value = data;
};

const router = useRouter();
const goToStory = (id) => {
  router.push({ name: "story-detail", params: { id } });
};
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