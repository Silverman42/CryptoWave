<template>
  <div
    class="rounded-3xl flex flex-col shadow-xl items-center bg-purple-600 p-6 py-10"
  >
    <span class="inline-block text-yellow-500 mb-5">
      <iconify :icon="barChart" width="30" height="30" />
    </span>
    <p class="text-white text-lg font-bold">$ 138,716,787,187</p>
    <span class="text-purple-300 text-sm">Total market cap</span>
  </div>
</template>

<script>
import barChart from '@iconify/icons-feather/bar-chart-2'
export default {
  name: 'MarketCapWidget',
  data() {
    return {
      barChart,
    }
  },
}
</script>

<style></style>
