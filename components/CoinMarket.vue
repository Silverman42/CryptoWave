<template>
  <div
    class="block border bg-white hover:border-purple-600 w-full p-5 pb-20 rounded-2xl coin"
  >
    <div class="flex justify-between">
      <div class="w-5/12 mr-2 flex">
        <img
          src="https://c2.coinlore.com/img/exchanges/25x25/binance.png"
          class="w-10 h-10 rounded-full bg-purple-600 object-contain object-center p-2 mr-3"
        />
        <div>
          <h6 class="text-purple-700 text-sm mb-1">Binance</h6>
          <p class="text-xs text-gray-500">BTC / USDT</p>
        </div>
      </div>
      <div
        class="w-6/12 text-right text-purple-900 text-lg text-purple-00 font-bold"
      >
        $ 56,564.30
      </div>
    </div>
    <div class="flex mt-5">
      <div class="flex-grow flex overflow-x-auto">
        <div class="mr-5">
          <p class="text-xs font-bold text-purple-900 whitespace-no-wrap">
            61764.1
          </p>
          <span class="text-xs text-gray-500">Exchange Price</span>
        </div>
        <div class="mr-5">
          <p class="text-xs font-bold text-purple-900 whitespace-no-wrap">
            4674.814035
          </p>
          <span class="text-xs text-gray-500">Volume</span>
        </div>
        <div class="mr-5">
          <p class="text-xs font-bold text-purple-900 whitespace-no-wrap">
            288735681.53914
          </p>
          <span class="text-xs text-gray-500">Volume (USD)</span>
        </div>
        <div class="mr-5">
          <p class="text-xs font-bold text-purple-900 whitespace-no-wrap">
            2-Dec-2021
          </p>
          <span class="text-xs text-gray-500">Time</span>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {},
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
