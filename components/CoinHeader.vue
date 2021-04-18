<template>
  <div class="block border bg-purple-700 w-full p-5 rounded-2xl">
    <div class="flex justify-between">
      <div class="w-5/12 mr-2 flex">
        <figure class="w-10 h-10 rounded-full bg-purple-300 mr-3"></figure>
        <div>
          <h6 class="text-white text-sm font-bold mb-1">Bitcoin</h6>
          <p class="text-xs text-purple-300">BTC</p>
        </div>
      </div>
      <div class="w-6/12 text-right text-lg text-yellow-300 font-bold">
        $ 56,564.30
      </div>
    </div>
    <div class="flex my-5">
      <div class="flex-grow w-full text-white flex overflow-x-auto">
        <div class="mr-5">
          <p class="text-xs font-bold whitespace-no-wrap">$ 138,716,787,187</p>
          <span class="text-xs text-purple-300">Market Cap</span>
        </div>
        <div class="mr-5">
          <p class="text-xs font-bold whitespace-no-wrap">$ 138,716,787,187</p>
          <span class="text-xs text-purple-300">Volume 24h</span>
        </div>
        <div class="mr-5">
          <p class="text-xs font-bold whitespace-no-wrap">4.50%</p>
          <span class="text-xs text-purple-300">24h%</span>
        </div>
        <div class="mr-5">
          <p class="text-xs font-bold whitespace-no-wrap">10.51%</p>
          <span class="text-xs text-purple-300">7d%</span>
        </div>
        <div class="mr-5">
          <p class="text-xs font-bold whitespace-no-wrap">0.39%</p>
          <span class="text-xs text-purple-300">1h%</span>
        </div>
        <div class="mr-5">
          <p class="text-xs font-bold whitespace-no-wrap">1</p>
          <span class="text-xs text-purple-300">Rank</span>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'CoinHeader',
}
</script>

<style></style>
