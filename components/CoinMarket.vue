<template>
  <div
    class="block border bg-white hover:border-purple-600 w-full p-5 pb-20 rounded-2xl coin bounce-up"
    :style="{ animationDelay: `${delay}s` }"
  >
    <div class="flex justify-between">
      <div class="w-5/12 mr-2 flex">
        <img
          :src="`https://c2.coinlore.com/img/exchanges/25x25/${nameId}.png`"
          class="w-10 h-10 rounded-full bg-purple-600 object-contain object-center p-2 mr-3"
        />
        <div>
          <h6 class="text-purple-700 text-sm mb-1 capitalize">
            {{ data.name }}
          </h6>
          <p class="text-xs text-gray-500 uppercase">
            {{ data.base }} / {{ data.quote }}
          </p>
        </div>
      </div>
      <div
        class="w-6/12 text-right text-purple-900 text-lg text-purple-00 font-bold"
      >
        ${{ data.price_usd | formatNumber }}
      </div>
    </div>
    <div class="flex mt-5">
      <div class="flex-grow flex overflow-x-auto">
        <div class="mr-5">
          <p class="text-xs font-bold text-purple-900 whitespace-no-wrap">
            {{ data.price | formatNumber }}
          </p>
          <span class="text-xs text-gray-500 whitespace-no-wrap"
            >Exchange Price</span
          >
        </div>
        <div class="mr-5">
          <p class="text-xs font-bold text-purple-900 whitespace-no-wrap">
            {{ data.volume | formatNumber }}
          </p>
          <span class="text-xs text-gray-500 whitespace-no-wrap">Volume</span>
        </div>
        <div class="mr-5">
          <p class="text-xs font-bold text-purple-900 whitespace-no-wrap">
            ${{ data.volume_usd | formatNumber }}
          </p>
          <span class="text-xs text-gray-500 whitespace-no-wrap"
            >Volume (USD)</span
          >
        </div>
        <div class="mr-5">
          <p class="text-xs font-bold text-purple-900 whitespace-no-wrap">
            {{ date }}
          </p>
          <span class="text-xs text-gray-500">Time</span>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
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
    delay: {
      type: [String, Number],
      default: '0.1',
    },
    data: {
      type: Object,
      default() {
        return {
          name: 'Coinbase Pro',
          base: 'BTC',
          quote: 'USD',
          price: '54916.62',
          price_usd: '54916.62',
          volume: '13914.00722601',
          volume_usd: '764110247.50805',
          time: '1619523412',
        }
      },
    },
  },
  computed: {
    nameId() {
      return this.data.name.toLowerCase().replace(' ', '-')
    },
    date() {
      return new Date(this.data.time).toLocaleString()
    },
  },
}
</script>

<style>
.coin {
  margin-top: -60px;
}
.coin:first-child {
  margin-top: 0px;
}
.coin:last-child {
  @apply pb-10;
}
</style>
