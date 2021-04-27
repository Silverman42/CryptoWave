<template>
  <div
    class="rounded-3xl flex flex-col shadow-xl items-center bg-purple-600 p-6 py-10"
  >
    <span class="inline-block text-yellow-500 mb-5">
      <iconify :icon="barChart" width="30" height="30" />
    </span>
    <p class="text-white text-lg font-bold">$ {{ marketCap | formatNumber }}</p>
    <span class="text-purple-300 text-sm">Total market cap</span>
  </div>
</template>

<script>
import barChart from '@iconify/icons-feather/bar-chart-2'
export default {
  name: 'MarketCapWidget',
  filters: {
    formatNumber(number, parseType = 'float') {
      const parsedNumber =
        parseType === 'int' ? parseInt(number) : parseFloat(number)
      const formatted = new Intl.NumberFormat('en-US', {
        style: 'decimal',
        maximumFractionDigits: 2,
      }).format(parsedNumber)
      return formatted
    },
  },
  props: {
    marketCap: {
      type: [String, Number],
      default: 0,
    },
  },
  data() {
    return {
      barChart,
    }
  },
}
</script>

<style></style>
