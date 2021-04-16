<template>
  <a
    href="#"
    class="rounded-lg flex flex-col hover:shadow-xl h-56 border border-gray-300 p-5 hover:border-purple-700 bg-white"
  >
    <div class="flex justify-between items-center mb-3">
      <div>
        <span class="capitalize text-sm text-purple-900 block font-bold"
          >Binance</span
        >
        <span class="text-xs text-gray-600">China</span>
      </div>
      <div class="inline-flex">
        <img
          src="https://www.coinlore.com/img/25x25/bitcoin.png"
          alt=""
          class="w-10 h-10 border-4 border-white rounded-full bg-purple-700"
          srcset=""
        />
      </div>
    </div>
    <div>
      <span class="text-lg block text-purple-700 font-bold"
        >5192501791.0689</span
      >
      <span class="text-gray-600 block text-xs">Volume</span>
    </div>

    <div class="mt-auto flex justify-between items-center">
      <div>
        <p class="text-purple-900">2 Dec 2019</p>
        <span class="text-xs text-gray-600 block">Added</span>
      </div>
      <button
        class="border py-3 px-6 capitalize flex text-xs items-center rounded-full hover:border-purple-800 hover:text-purple-800"
      >
        <span class="mr-2">View</span>
        <span>></span>
      </button>
    </div>
  </a>
</template>

<script>
export default {
  name: 'Market',
}
</script>

<style></style>
