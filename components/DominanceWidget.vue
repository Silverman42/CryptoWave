<template>
  <div
    class="rounded-3xl overflow-hidden flex bg-white border border-gray-300 shadow-xl"
  >
    <div class="p-5 bg-white flex flex-col w-1/2">
      <img
        src="/img/icon/cryptocurrency_btc.svg"
        class="mb-4 w-8"
        alt="bitcoin_logo"
      />
      <p class="text-lg text-gray-800 font-bold">61.08%</p>
      <span class="text-gray-500 text-xs">BTC Dominance</span>
    </div>
    <div class="p-5 bg-purple-600 flex flex-col items-end text-right w-1/2">
      <img
        src="/img/icon/cryptocurrency_eth.svg"
        class="mb-4 w-8"
        alt="Ethereum logo"
      />
      <p class="text-lg text-white font-bold">12.07%</p>
      <span class="text-purple-200 text-xs">ETH Dominance</span>
    </div>
  </div>
</template>

<script>
export default {
  name: 'DominanceWidget',
}
</script>

<style></style>
