<template>
  <nuxt-link
    :to="to"
    class="block border bg-white hover:border-purple-600 w-full p-5 pb-20 rounded-2xl coin bounce-up"
    :style="{ animationDelay: `${delay}s` }"
  >
    <div class="flex justify-between">
      <div class="w-5/12 mr-2 flex">
        <figure class="w-10 h-10 rounded-full bg-purple-700 mr-3"></figure>
        <div>
          <h6 class="text-purple-700 text-sm mb-1">Bitcoin</h6>
          <p class="text-xs text-gray-500">BTC</p>
        </div>
      </div>
      <div class="w-6/12 text-right text-lg text-purple-900 font-bold">
        $ 56,564.30
      </div>
    </div>
    <div class="flex mt-5">
      <div class="flex-grow flex overflow-x-auto">
        <div class="mr-5">
          <p class="text-xs font-bold text-purple-900 whitespace-nowrap">
            $138,716,787,187
          </p>
          <span class="text-xs text-gray-500">Market Cap</span>
        </div>
        <div class="mr-5">
          <p class="text-xs font-bold text-purple-900 whitespace-nowrap">
            $138,716,787,187
          </p>
          <span class="text-xs text-gray-500">Volume 24h</span>
        </div>
        <div class="mr-5">
          <p class="text-xs font-bold text-purple-900 whitespace-nowrap">
            4.50%
          </p>
          <span class="text-xs text-gray-500">24h%</span>
        </div>
        <div class="mr-5">
          <p class="text-xs font-bold text-purple-900 whitespace-nowrap">
            10.51%
          </p>
          <span class="text-xs text-gray-500">7d%</span>
        </div>
        <div class="mr-5">
          <p class="text-xs font-bold text-purple-900 whitespace-nowrap">
            0.39%
          </p>
          <span class="text-xs text-gray-500">1h%</span>
        </div>
        <div class="mr-5">
          <p class="text-xs font-bold text-purple-900 whitespace-nowrap">1</p>
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
