<template>
  <div class="block border bg-purple-700 w-full p-5 rounded-2xl">
    <div class="flex justify-between">
      <div class="w-5/12 mr-2 flex">
        <img
          :src="`https://www.coinlore.com/img/25x25/${data.nameid}.png`"
          class="w-10 h-10 rounded-full bg-purple-400 object-contain object-center p-2 mr-3"
        />
        <div>
          <h6 class="text-white text-sm font-bold mb-1 capitalize">
            {{ data.name }}
          </h6>
          <p class="text-xs text-purple-300 uppercase">{{ data.symbol }}</p>
        </div>
      </div>
      <div class="w-6/12 text-right text-lg text-yellow-300 font-bold">
        $ {{ data.price_usd | formatNumber }}
      </div>
    </div>
    <div class="flex my-5">
      <div class="flex-grow w-full text-white flex overflow-x-auto">
        <div class="mr-5">
          <p class="text-xs font-bold whitespace-no-wrap">
            $ {{ data.market_cap_usd | formatNumber }}
          </p>
          <span class="text-xs text-purple-300">Market Cap</span>
        </div>
        <div class="mr-5">
          <p class="text-xs font-bold whitespace-no-wrap">
            $ {{ data.volume24 | formatNumber }}
          </p>
          <span class="text-xs text-purple-300">Volume 24h</span>
        </div>
        <div class="mr-5">
          <p class="text-xs font-bold whitespace-no-wrap">
            {{ data.percent_change_24h }}%
          </p>
          <span class="text-xs text-purple-300">24h%</span>
        </div>
        <div class="mr-5">
          <p class="text-xs font-bold whitespace-no-wrap">
            {{ data.percent_change_7d }}%
          </p>
          <span class="text-xs text-purple-300">7d%</span>
        </div>
        <div class="mr-5">
          <p class="text-xs font-bold whitespace-no-wrap">
            {{ data.percent_change_1h }}%
          </p>
          <span class="text-xs text-purple-300">1h%</span>
        </div>
        <div class="mr-5">
          <p class="text-xs font-bold whitespace-no-wrap">{{ data.rank }}</p>
          <span class="text-xs text-purple-300">Rank</span>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'CoinHeader',
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
    data: {
      type: Object,
      default() {
        return {
          symbol: '',
          name: '',
          nameid: '',
          rank: 1,
          price_usd: '0.0',
          percent_change_24h: '0.0',
          percent_change_1h: '0.0',
          percent_change_7d: '0.0',
          market_cap_usd: '0.0',
          volume24: '0.00',
          volume24_native: '0.00',
          csupply: '0.00',
          price_btc: '0.00',
          tsupply: '0',
          msupply: '0',
        }
      },
    },
  },
}
</script>

<style></style>
