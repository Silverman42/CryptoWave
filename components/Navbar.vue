<template>
  <nav class="flex justify-between items-center max-w-6xl mx-auto p-4">
    <a href="#" class="w-30 md:inline-block"> CryptoWave </a>
    <ul
      class="w-full border-t md:border-0 md:w-auto fixed bg-white md:relative right-0 bottom-0 justify-around md:justify-end list-none py-3 flex items-center"
    >
      <li class="md:mr-10">
        <a
          href="#"
          class="text-xs md:text-sm hover:text-purple-700 text-gray-800"
          >Home</a
        >
      </li>
      <li class="md:mr-10">
        <a
          href="#"
          class="text-xs md:text-sm hover:text-purple-700 text-gray-800"
          >Markets</a
        >
      </li>
      <li>
        <a
          href="#"
          class="text-xs md:text-sm hover:text-purple-600 text-gray-800"
          >Saved</a
        >
      </li>
    </ul>
  </nav>
</template>

<script>
export default {
  name: 'Navbar',
}
</script>
