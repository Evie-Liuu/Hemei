<template>
  <div class="flex justify-center items-center gap-4 mt-8">
    <button
      @click="prevPage"
      :disabled="currentPage === 1"
      class="px-4 py-2 bg-gray-300 rounded-md disabled:opacity-50"
    >
      上一頁
    </button>
    <span>第 {{ currentPage }} / {{ totalPages }} 頁</span>
    <button
      @click="nextPage"
      :disabled="currentPage === totalPages"
      class="px-4 py-2 bg-gray-300 rounded-md disabled:opacity-50"
    >
      下一頁
    </button>
  </div>
</template>
<script setup>
import { computed, defineProps, defineEmits } from "vue";

const props = defineProps({
  filteredInfo: {
    type: Object,
    default: () => ({}),
  },
});

const emits = defineEmits(["update:paginatedInfo"]);
watch(paginatedInfo, (newValue) => {
  const numericValue = Number(newValue);
  emits("update:paginatedInfo", numericValue);
});

const currentPage = ref(1);
const itemsPerPage = 3;

const totalPages = computed(() => {
  return Math.ceil(props.filteredInfo.length / itemsPerPage);
});

const paginatedInfo = computed(() => {
  const startIndex = (currentPage.value - 1) * itemsPerPage;
  const endIndex = startIndex + itemsPerPage;
  return props.filteredInfo.slice(startIndex, endIndex);
});

const nextPage = () => {
  if (currentPage.value < totalPages.value) {
    currentPage.value++;
  }
};

const prevPage = () => {
  if (currentPage.value > 1) {
    currentPage.value--;
  }
};
</script>
<style scoped>
</style>