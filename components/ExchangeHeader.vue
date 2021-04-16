<template>
  <div class="block border bg-purple-700 w-full p-5 rounded-2xl shadow-xl">
    <div class="flex justify-between items-center">
      <div class="w-5/12 mr-2 flex">
        <img
          class="w-10 h-10 rounded-full p-1 bg-white mr-3"
          src="https://c2.coinlore.com/img/exchanges/25x25/binance.png"
        />
        <div>
          <h6 class="text-white text-sm font-bold mb-1">Binance</h6>
          <p class="text-xs text-purple-300">China</p>
        </div>
      </div>
      <div class="w-6/12 text-right">
        <a
          href="#"
          class="border text-sm py-3 px-6 capitalize inline-flex items-center rounded-full whitespace-no-wrap border-purple-400 text-purple-300 hover:border-white hover:text-white"
        >
          <span class="mr-2">Visit Website</span>
          <span>></span>
        </a>
      </div>
    </div>
    <div class="my-5">
      <span class="block text-lg text-yellow-300 font-bold">
        $45,989,302,557.44771
      </span>
      <span class="text-xs text-purple-300">Volume</span>
    </div>
    <div class="flex my-5">
      <div class="flex-grow w-full text-white flex overflow-x-auto">
        <div class="mr-5">
          <p class="text-xs font-bold whitespace-nowrap">
            $1,193,509,971,994.565
          </p>
          <span class="text-xs text-purple-300">Adj. Volume</span>
        </div>
        <div class="mr-5">
          <p class="text-xs font-bold whitespace-no-wrap">926</p>
          <span class="text-xs text-purple-300">Pairs</span>
        </div>
        <div class="mr-5">
          <p class="text-xs font-bold whitespace-no-wrap">True</p>
          <span class="text-xs text-purple-300">USDT</span>
        </div>
        <div class="mr-5">
          <p class="text-xs font-bold whitespace-no-wrap">True</p>
          <span class="text-xs text-purple-300">Fiat</span>
        </div>
        <div class="mr-5">
          <p class="text-xs font-bold whitespace-no-wrap">2-Dec-2012</p>
          <span class="text-xs text-purple-300">Founded</span>
        </div>
        <div class="mr-5">
          <p class="text-xs font-bold whitespace-no-wrap">2-Dec-2012</p>
          <span class="text-xs text-purple-300">Date Live</span>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'ExchangeHeader',
}
</script>

<style></style>
