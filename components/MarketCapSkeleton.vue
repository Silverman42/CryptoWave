<template>
  <div
    class="rounded-3xl flex flex-col shadow-xl items-center bg-purple-600 p-6 py-10"
  >
    <span class="inline-block text-yellow-500 mb-5">
      <iconify :icon="barChart" width="30" height="30" />
    </span>
    <div class="p-2 w-8/12 my-4 animate-pulse rounded-full bg-purple-300"></div>
    <div class="p-2 w-4/12 animate-pulse rounded-full bg-purple-300"></div>
  </div>
</template>

<script>
import barChart from '@iconify/icons-feather/bar-chart-2'
export default {
  data() {
    return {
      barChart,
    }
  },
}
</script>

<style></style>
