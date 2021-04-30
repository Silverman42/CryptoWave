<template>
  <div
    tabindex="-1"
    class="rounded-lg cursor-pointer outline-none flex flex-col hover:shadow-xl h-56 border border-gray-300 p-5 hover:border-purple-700 bg-white bounce-up"
    :style="{ animationDelay: `${delay}s` }"
    @click="viewMarketData"
  >
    <div class="flex justify-between mb-3">
      <div>
        <span class="capitalize text-sm text-purple-900 block font-bold">{{
          data.name
        }}</span>
        <span class="text-xs text-gray-600 capitalize">{{ data.country }}</span>
      </div>
      <div class="inline-flex">
        <img
          :src="`https://www.coinlore.com/img/exchanges/${data.name_id}.png`"
          :alt="data.name"
          class="w-10 h-10 rounded-full bg-purple-400 object-contain object-center p-2"
          srcset=""
          @error="setDefaultImage($event)"
        />
      </div>
    </div>
    <div class="mt-auto">
      <span class="text-lg block text-purple-700 font-bold">{{
        data.volume_usd | formatNumber
      }}</span>
      <span class="text-gray-600 block text-xs">Volume</span>
    </div>

    <div class="mt-auto flex justify-between items-center">
      <div>
        <p class="text-purple-900">{{ data.date_added | formatDate }}</p>
        <span class="text-xs text-gray-600 block">Added</span>
      </div>
      <button
        class="border py-3 px-6 capitalize flex text-xs items-center rounded-full hover:border-purple-800 hover:text-purple-800"
      >
        <span class="mr-2">View</span>
        <span>></span>
      </button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Market',
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
    formatDate(date) {
      if (date === '0000-00-00 00:00:00') {
        return 'Unknown Date'
      }
      const newDate = new Date(date)
      return new Intl.DateTimeFormat('en-GB', {
        year: 'numeric',
        month: 'short',
        day: 'numeric',
      }).format(newDate)
    },
  },
  props: {
    delay: {
      type: [String, Number],
      default: '0.1',
    },
    data: {
      type: Object,
      default() {
        return {
          name: '',
          name_id: '',
          url: '',
          country: '',
          date_live: '0000-00-00 00:00:00',
          volume_usd: '',
          fiat: '0',
          volume_usd_adj: '',
          pairs: '',
          usdt: '',
          date_added: '0000-00-00 00:00:00',
          id: '',
        }
      },
    },
  },
  methods: {
    viewMarketData() {
      this.$emit('viewMarket', this.data)
    },
    setDefaultImage(event) {
      event.target.onerror = null
      event.target.src = './img/coin.svg'
    },
  },
}
</script>

<style></style>
