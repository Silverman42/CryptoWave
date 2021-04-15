<template>
  <div class="rounded-3xl bg-white border border-gray-300 shadow-xl px-5 py-10">
    <div class="flex flex-col items-center mb-6">
      <span
        class="w-10 mb-3 flex justify-center items-center h-10 rounded-xl bg-yellow-100"
      >
        <span class="rounded-full w-6 h-6 border-4 border-yellow-400"></span>
      </span>
      <p class="text-purple-700 font-bold text-lg">$ 138,716,787,187</p>
      <span class="text-gray-500 text-xs">Total volume for the last 24Hrs</span>
    </div>
    <div class="flex justify-between items-center mb-6">
      <div>
        <p class="text-xs text-purple-900 font-bold">5948</p>
        <span class="text-gray-500 text-xs">Coin count</span>
      </div>
      <div class="text-right">
        <p class="text-xs text-purple-900 font-bold">20672</p>
        <span class="text-gray-500 text-xs">Active Market</span>
      </div>
    </div>
    <div class="flex justify-between items-center">
      <div>
        <p class="text-xs text-purple-900 font-bold">$ 138,716,787,187</p>
        <span class="text-gray-500 text-xs">Market Cap. ATH</span>
      </div>
      <div class="text-right">
        <p class="text-xs text-purple-900 font-bold">$ 138,716,787,187</p>
        <span class="text-gray-500 text-xs">Volume ATH</span>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'TotalVolumeWidget',
}
</script>

<style></style>
