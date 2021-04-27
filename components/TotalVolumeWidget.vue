<template>
  <div class="rounded-3xl bg-white border border-gray-300 shadow-xl px-5 py-10">
    <div class="flex flex-col items-center mb-6">
      <span
        class="w-10 mb-3 flex justify-center text-yellow-400 items-center h-10 rounded-xl bg-yellow-200"
      >
        <iconify :icon="briefCase" width="28" height="28" />
      </span>
      <p class="text-purple-700 font-bold text-lg">
        $ {{ volume.total_volume | formatNumber }}
      </p>
      <span class="text-gray-500 text-xs">Total volume for the last 24Hrs</span>
    </div>
    <div class="flex justify-between items-center mb-6">
      <div>
        <p class="text-xs text-purple-900 font-bold">
          {{ volume.coins_count | formatNumber('int') }}
        </p>
        <span class="text-gray-500 text-xs">Coin count</span>
      </div>
      <div class="text-right">
        <p class="text-xs text-purple-900 font-bold">
          {{ volume.active_markets | formatNumber('int') }}
        </p>
        <span class="text-gray-500 text-xs">Active Market</span>
      </div>
    </div>
    <div class="flex justify-between flex-col text-center items-center">
      <div class="mb-6">
        <p class="text-xs text-purple-900 font-bold">
          $ {{ volume.mcap_ath | formatNumber }}
        </p>
        <span class="text-gray-500 text-xs">Market Cap. ATH</span>
      </div>
      <div>
        <p class="text-xs text-purple-900 font-bold">
          $ {{ volume.volume_ath | formatNumber }}
        </p>
        <span class="text-gray-500 text-xs">Volume ATH</span>
      </div>
    </div>
  </div>
</template>

<script>
import briefCase from '@iconify/icons-feather/briefcase'
export default {
  name: 'TotalVolumeWidget',
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
    volume: {
      type: Object,
      default() {
        return {
          mcap_ath: 0,
          volume_ath: 0,
          coins_count: 0,
          active_markets: 0,
          total_volume: 0,
        }
      },
    },
  },
  data() {
    return {
      briefCase,
    }
  },
}
</script>

<style></style>
