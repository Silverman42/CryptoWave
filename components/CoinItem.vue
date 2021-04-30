<template>
  <nuxt-link
    :to="to"
    class="block border bg-white hover:border-purple-600 w-full p-5 pb-20 rounded-2xl coin bounce-up"
    :style="{ animationDelay: `${delay}s` }"
  >
    <div class="flex justify-between">
      <div class="w-5/12 mr-2 flex">
        <img
          :src="`https://www.coinlore.com/img/25x25/${data.nameid}.png`"
          class="w-10 h-10 rounded-full bg-purple-400 object-contain object-center p-2 mr-3"
        />
        <div>
          <h6 class="text-purple-700 text-sm mb-1 capitalize">
            {{ data.name }}
          </h6>
          <p class="text-xs text-gray-500 uppercase">{{ data.symbol }}</p>
        </div>
      </div>
      <div class="w-6/12 text-right text-lg text-purple-900 font-bold">
        ${{ data.price_usd | formatNumber }}
      </div>
    </div>
    <div class="flex mt-5">
      <div class="flex-grow flex overflow-x-auto">
        <div class="mr-5">
          <p class="text-xs font-bold text-purple-900 whitespace-no-wrap">
            ${{ data.market_cap_usd | formatNumber }}
          </p>
          <span class="text-xs text-gray-500">Market Cap</span>
        </div>
        <div class="mr-5">
          <p class="text-xs font-bold text-purple-900 whitespace-no-wrap">
            ${{ data.volume24 | formatNumber }}
          </p>
          <span class="text-xs text-gray-500">Volume 24h</span>
        </div>
        <div class="mr-5">
          <p class="text-xs font-bold text-purple-900 whitespace-no-wrap">
            {{ data.percent_change_24h }}%
          </p>
          <span class="text-xs text-gray-500">24h%</span>
        </div>
        <div class="mr-5">
          <p class="text-xs font-bold text-purple-900 whitespace-no-wrap">
            {{ data.percent_change_7d }}%
          </p>
          <span class="text-xs text-gray-500">7d%</span>
        </div>
        <div class="mr-5">
          <p class="text-xs font-bold text-purple-900 whitespace-no-wrap">
            {{ data.percent_change_1h }}%
          </p>
          <span class="text-xs text-gray-500">1h%</span>
        </div>
        <div class="mr-5">
          <p class="text-xs font-bold text-purple-900 whitespace-no-wrap">
            {{ data.rank }}
          </p>
          <span class="text-xs text-gray-500">Rank</span>
        </div>
      </div>
      <div class="w-40 text-right">
        <a href="" class="text-purple-500 hover:text-purple-700">View</a>
      </div>
    </div>
  </nuxt-link>
</template>

<script>
export default {
  name: 'CoinItem',
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
    to: {
      type: Object,
      default() {
        return {
          path: '/',
        }
      },
    },
    data: {
      type: Object,
      default() {
        return {
          symbol: '',
          name: '',
          nameid: '',
          rank: 0,
          price_usd: '0',
          percent_change_24h: '10.17',
          percent_change_1h: '4.80',
          percent_change_7d: '-15.71',
          price_btc: '0.000340',
          market_cap_usd: '71236597.71',
          volume24: 3649387.04282345,
          volume24a: 5735363.513063776,
        }
      },
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
