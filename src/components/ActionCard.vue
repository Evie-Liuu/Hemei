<template>
  <div
    class="animate-fade-in-up cursor-pointer w-full md:max-w-7xl md:mx-auto min-h-96 md:min-h-80 bg-white rounded-xl shadow-md overflow-hidden flex flex-col md:flex-row hover:scale-105"
    v-for="info in filteredInfo"
    :key="info.id"
    @click="goToActions(info.id)"
  >
    <div class="relative w-full h-64 md:h-auto md:w-1/2">
      <img
        src="@/assets/images/cover.png"
        alt="Card Image"
        class="absolute inset-0 w-full h-full object-cover object-center"
      />
    </div>
    <div class="p-6 md:p-15 flex flex-col justify-center w-full">
      <h2 class="text-md mb-2">主題：{{ info.title }}</h2>
      <p class="text-md mb-2">
        時間：{{
          info.startTime.length
            ? new Date(info.startTime * 1000).toLocaleDateString() +
              " ~ " +
              new Date(info.endTime * 1000).toLocaleDateString()
            : "無"
        }}
      </p>
      <p class="text-md mb-2">成員：{{ info.group }}</p>
      <p class="text-md mb-2">描述：{{ info.intro }}</p>
      <div class="flex items-center w-full md:w-70 gap-3">
        進度：
        <!-- Progress Bar -->
        <div
          class="relative flex-1 bg-gray-200 rounded-full h-2 overflow-hidden"
        >
          <div
            class="h-2 rounded-full transition-all duration-500"
            :class="progressColor(info.progress)"
            :style="{ width: info.progress + '%' }"
          ></div>
        </div>
        <!-- Percentage Number -->
        <span class="w-10 text-sm text-gray-700 text-left">
          {{ info.progress }}%
        </span>
      </div>
      <div class="flex flex-wrap gap-2 mt-2">
        <span
          v-for="t in info.types"
          :key="t"
          class="px-3 py-1 text-sm rounded-full bg-blue-100 text-blue-800"
        >
          {{ typeTags[t].title }}
        </span>
      </div>
      <p class="text-gray-600 text-sm text-right">更多</p>
    </div>
  </div>
</template>
<script setup>
import { defineProps } from "vue";
import { useRouter } from "vue-router";
const router = useRouter();

import typeTags from "@/data/SDGs_goal.json";

const props = defineProps({
  filteredInfo: {
    type: Array,
    default: () => [],
  },
});

const progressColor = (progress) => {
  if (progress < 40) return "bg-red-500";
  if (progress < 70) return "bg-yellow-400";
  return "bg-green-500";
};
const goToActions = (id) => {
  return;
  router.push({ name: "story-detail", params: { id } });
};
</script>
<style scoped>
</style>