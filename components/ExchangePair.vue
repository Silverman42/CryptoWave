<template>
  <a
    href="#"
    class="rounded-lg flex flex-col h-52 hover:shadow-xl border border-gray-300 p-5 hover:border-purple-700 bg-white bounce-up"
    :style="{ animationDelay: `${delay}s` }"
  >
    <div class="flex justify-between items-center mb-3">
      <p class="uppercase text-xs text-purple-900 font-bold uppercase">
        {{ data.base }} / {{ data.quote }}
      </p>
      <div class="inline-flex">
        <img
          src="/img/coin.svg"
          alt=""
          class="w-10 h-10 rounded-full bg-yellow-200 object-contain object-center p-1"
          srcset=""
        />
        <img
          src="/img/coin_purple.svg"
          alt=""
          class="-ml-4 w-10 h-10 rounded-full bg-purple-200 object-contain object-center p-1"
          srcset=""
        />
      </div>
    </div>
    <p class="font-bold text-lg text-purple-700 mb-3">
      ${{ data.price_usd | formatNumber }}
    </p>
    <div class="mt-auto">
      <span class="text-sm block text-purple-900 font-bold">{{
        data.volume | formatNumber
      }}</span>
      <span class="text-gray-600 block text-xs">Volume</span>
    </div>
  </a>
</template>

<script>
export default {
  name: 'ExchangePair',
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
          base: '',
          quote: '',
          volume: '0.0',
          price: '0.0',
          price_usd: '0.0',
        }
      },
    },
  },
}
</script>

<style></style>
