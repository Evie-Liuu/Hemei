<template>
  <main
    class="grid grid-flow-col grid-rows-2 lg:pt-20 h-screen w-screen text-center bg-[url('@/assets/images/Mobile/Background_All_Phone.png')] bg-cover bg-center overflow-hidden lg:bg-[url('@/assets/images/Main-Page_Base_All.png')]"
  >
    <!-- Cover -->
    <section class="row-span-3">
      <h1>123</h1>
    </section>
    <!-- School Title -->
    <section class="col-span-1">
      <div
        :class="[
          'transition-all duration-1000 ease-out',
          isLoaded
            ? 'opacity-100 translate-y-0'
            : 'opacity-0 -translate-y-full',
        ]"
        class="font-bold text-brown-500 flex flex-col items-center lg:gap-5 lg:flex-row lg:justify-start w-full lg:ps-54"
      >
        <picture>
          <img
            src=""
            class="pointer-events-none select-none max-w-25 lg:max-w-50"
            alt="Owl"
          />
        </picture>
        <div class="inline-block my-auto">
          <h1 class="text-4xl lg:text-4xl">彰化市和美國民小學</h1>
          <small
            class="block text-brown-400 text-xl lg:text-xl"
            style="text-align: justify; text-align-last: justify"
            >Changhua Hemei Elementary School</small
          >
        </div>
      </div>
    </section>
    <!-- Menu Buttons -->
    <section class="col-span-1 row-span-1">
      <div class="flex flex-col gap-5 items-center justify-center">
        <router-link to="/about" class="relative hover:text-brown-600">
          <img
            src=""
            class="pointer-events-none select-none"
            alt="Speak_bubble_1"
          />
          <span
            class="absolute flex items-center justify-center text-black font-bold ps-5"
            >校園探索</span
          >
        </router-link>
        <router-link to="/actions" class="relative"
          ><img
            src=""
            class="pointer-events-none select-none"
            alt="Speak_bubble_1"
          />
          <span
            class="absolute flex items-center justify-center text-black font-bold ps-5"
            >SDGs行動</span
          ></router-link
        >
        <router-link to="/sdgs" class="relative"
          ><img
            src=""
            class="pointer-events-none select-none"
            alt="Speak_bubble_1"
          />
          <span
            class="absolute flex items-center justify-center text-black font-bold ps-5"
            >SDGs成果</span
          ></router-link
        >
      </div>
    </section>


    <!-- Menu Buttons for Mobile -->
    <div></div>
  </main>
</template>
<script setup>
import { ref, onMounted } from "vue";

const isLoaded = ref(false);

onMounted(() => {
  setTimeout(() => {
    isLoaded.value = true;
  }, 100);
});
</script>
<style scoped>
</style>
