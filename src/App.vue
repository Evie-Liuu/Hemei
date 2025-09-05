<template>
  <div
    v-if="isLoading && $route.path !== '/' && $route.path !== '/about'"
    class="loading-overlay"
  >
    <img src="" class="loader" alt="Loading..." />
    <p>Loading...</p>
  </div>
  <nav
    class="absolute z-10 w-full p-2 font-bold text-rice-500 md:text-4xl flex flex-row justify-between items-center"
    :class="[$route.path !== '/' ? 'bg-header' : '']"
  >
    <router-link to="/" @click="isMenuOpen = false" class="flex flex-row gap-2">
      <img
        src="@/assets/images/School_Logo.png"
        alt="School Logo Watercolor"
        :class="{ hidden: $route.path === '/' }"
        class="relative z-20 inset-0 w-1/11 object-end md:w-1/15"
      />
      <div
        :class="{ hidden: $route.path === '/' }"
        class="relative z-20 my-auto md:text-3xl text-2xl font-hspa"
      >
        彰化市和美國民小學
      </div>
    </router-link>

    <!-- Hamburger Button -->
    <button
      v-if="$route.path !== '/'"
      @click="isMenuOpen = !isMenuOpen"
      class="md:hidden z-20"
    >
      <i class="fa-solid fa-bars"></i>
    </button>

    <!-- Menu -->
    <div
      :class="[
        'fixed top-0 left-0 w-full flex flex-col justify-center items-center gap-8 text-3xl transition-transform duration-300 ease-in-out md:relative md:h-[4rem] md:w-auto md:bg-transparent md:flex-row md:gap-3 md:text-2xl md:whitespace-nowrap',
        isMenuOpen ? 'h-full' : 'h-0',
        isMenuOpen ? 'translate-x-0' : '-translate-x-full md:translate-x-0',
        isMenuOpen
          ? 'bg-[url(@/assets/images/CS_school.png)] bg-cover bg-center overflow-hidden'
          : '',
      ]"
      class="text-white md:text-black md:text-shadow-none"
    >
      <div class="absolute z-[-10] inset-0 bg-black/40 md:hidden"></div>
      <router-link
        to="/"
        class="px-8 text-rice-500 text-shadow-3d"
        @click="isMenuOpen = false"
        :class="{
          'pointer-events-none bg-brown-400 opacity-80 rounded-full':
            $route.path === '/',
        }"
        >首頁</router-link
      >
      <router-link
        to="/about"
        class="px-4 text-rice-500 text-shadow-3d"
        @click="isMenuOpen = false"
        :class="{
          'pointer-events-none bg-brown-400  opacity-80 rounded-full':
            $route.path === '/about',
          'pointer-events-none bg-gradient-to-br from-green-600 to-yellow-400 opacity-80 rounded-full':
            isMenuOpen && $route.path === '/about',
        }"
        >校園探索</router-link
      >
      <router-link
        to="/actions"
        class="px-4 text-rice-500 text-shadow-3d"
        @click="isMenuOpen = false"
        :class="{
          'pointer-events-none bg-brown-400  opacity-80 rounded-full':
            $route.path === '/actions',
          'pointer-events-none bg-gradient-to-br from-green-600 to-yellow-400 opacity-80 rounded-full':
            isMenuOpen && $route.path === '/actions',
        }"
        >SDGs行動</router-link
      >
      <router-link
        to="/sdgs"
        class="px-4 text-rice-500 text-shadow-3d"
        @click="isMenuOpen = false"
        :class="{
          'pointer-events-none bg-brown-400 opacity-80 rounded-full':
            $route.path === '/sdgs' || $route.path.includes('/story'),
          'pointer-events-none bg-gradient-to-br from-green-600 to-yellow-400 opacity-80 rounded-full':
            isMenuOpen &&
            ($route.path === '/sdgs' || $route.path.includes('/story')),
        }"
        >SDGs成果</router-link
      >
    </div>
  </nav>
  <router-view />
</template>
<script setup>
import { ref, onMounted } from "vue";

const isLoading = ref(true);
const isMenuOpen = ref(false);

onMounted(() => {
  setTimeout(() => {
    isLoading.value = false;
  }, 1000);
});
</script>
<style scoped>
</style>