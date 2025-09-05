<template>
  <main
    class="grid grid-flow-col grid-rows-2 h-screen w-screen text-center bg-[url('@/assets/images/Mobile/Web_Bcakground.png')] bg-cover bg-center overflow-hidden lg:bg-[url('@/assets/images/Backgound.png')]"
  >
    <img src="@/assets/images/Frame.png" alt="Frame" class="hidden lg:block" />
    <!-- Cover -->
    <section class="row-span-3">
      <div
        :class="[
          'transition-all duration-1000 ease-out',
          isLoaded
            ? 'opacity-100 translate-x-0'
            : 'opacity-0 -translate-x-full',
        ]"
        class="lg:w-full lg:h-full flex items-center justify-center"
      >
        <img
          src="@/assets/images/ChinesePaintingRing.png"
          class="pointer-events-none select-none max-w-55 lg:max-w-350"
          alt="Hemei_cover"
        />
      </div>
    </section>
    <!-- School Title -->
    <section class="col-span-1 lg:-ml-48 z-10">
      <div
        :class="[
          'transition-all duration-1000 ease-out',
          isLoaded
            ? 'opacity-100 translate-y-0'
            : 'opacity-0 -translate-y-full',
        ]"
        class="font-bold text-brown-500 flex flex-col items-center lg:gap-5 lg:flex-row lg:justify-start w-full"
      >
        <picture>
          <img
            src="@/assets/images/Text_H.png"
            class="pointer-events-none select-none max-w-25 lg:max-w-50"
            alt="Hemei_Text_H"
          />
        </picture>
      </div>
    </section>
    <!-- Menu Buttons -->
    <section class="col-span-1 row-span-1 lg:-ml-48 z-10">
      <div class="flex flex-col gap-5 items-center justify-center">
        <router-link
          to="/about"
          class="relative"
          @mouseover="hoveredIndex = 0"
          @mouseleave="hoveredIndex = null"
        >
          <img
            :src="hoveredIndex === 0 ? paint1Selected : paint1Unselected"
            class="pointer-events-none select-none"
            alt="Paint_1"
          />
          <span
            class="absolute inset-0 flex items-center justify-center text-white font-bold ps-5"
            >校園探索</span
          >
        </router-link>
        <router-link
          to="/actions"
          class="relative"
          @mouseover="hoveredIndex = 1"
          @mouseleave="hoveredIndex = null"
          ><img
            :src="hoveredIndex === 1 ? paint2Selected : paint2Unselected"
            class="pointer-events-none select-none"
            alt="Paint_2"
          />
          <span
            class="absolute inset-0 flex items-center justify-center text-white font-bold ps-5"
            >SDGs行動</span
          ></router-link
        >
        <router-link
          to="/sdgs"
          class="relative"
          @mouseover="hoveredIndex = 2"
          @mouseleave="hoveredIndex = null"
          ><img
            :src="hoveredIndex === 2 ? paint3Selected : paint3Unselected"
            class="pointer-events-none select-none"
            alt="Paint_3"
          />
          <span
            class="absolute inset-0 flex items-center justify-center text-white font-bold ps-5"
            >SDGs成果</span
          ></router-link
        >
      </div>
    </section>
    <img src="@/assets/images/Frame.png" alt="Frame" class="hidden lg:block rotate-180" />

    <!-- Menu Buttons for Mobile -->
    <div></div>
  </main>
</template>
<script setup>
import { ref, onMounted } from "vue";
import paint1Unselected from "@/assets/images/Paint_1_Unselected.png";
import paint1Selected from "@/assets/images/Paint_1_Selected.png";
import paint2Unselected from "@/assets/images/Paint_2_Unselected.png";
import paint2Selected from "@/assets/images/Paint_2_Selected.png";
import paint3Unselected from "@/assets/images/Paint_3_Unselected.png";
import paint3Selected from "@/assets/images/Paint_3_Selected.png";

const hoveredIndex = ref(null);
const isLoaded = ref(false);

onMounted(() => {
  setTimeout(() => {
    isLoaded.value = true;
  }, 100);
});
</script>
<style scoped>
</style>
