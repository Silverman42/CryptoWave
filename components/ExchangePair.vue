<template>
  <a
    href="#"
    class="rounded-lg flex flex-col h-52 hover:shadow-xl border border-gray-300 p-5 hover:border-purple-700 bg-white"
  >
    <div class="flex justify-between items-center mb-3">
      <p class="uppercase text-xs text-purple-900 font-bold">BTC / USDT</p>
      <div class="inline-flex">
        <img
          src="https://www.coinlore.com/img/25x25/bitcoin.png"
          alt=""
          class="w-10 h-10 border-4 border-white rounded-full bg-purple-700"
          srcset=""
        />
        <img
          src="https://www.coinlore.com/img/25x25/ethereum.png"
          alt=""
          class="-ml-3 border-4 border-white w-10 h-10 rounded-full bg-purple-700"
          srcset=""
        />
      </div>
    </div>
    <p class="font-bold text-lg text-purple-700 mb-3">$ 579.9</p>
    <div class="mt-auto">
      <span class="text-sm block text-purple-900 font-bold"
        >5192501791.0689</span
      >
      <span class="text-gray-600 block text-xs">Volume</span>
    </div>
  </a>
</template>

<script>
export default {
  name: 'ExchangePair',
}
</script>

<style></style>
