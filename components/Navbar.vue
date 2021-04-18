<template>
  <nav class="flex justify-between items-center max-w-6xl mx-auto p-4">
    <nuxt-link to="/" class="w-30 md:inline-block">
      <img src="/img/logo.svg" class="w-full" alt="crypto wave logo" />
    </nuxt-link>
    <ul
      class="w-full border-t md:border-0 md:w-auto fixed bg-white md:bg-transparent md:relative right-0 bottom-0 justify-around md:justify-end list-none py-3 flex items-center"
    >
      <slot>
        <li class="md:mr-10">
          <a
            href="#"
            class="text-xs md:text-sm hover:text-purple-700 text-gray-800"
            >Home</a
          >
        </li>
      </slot>
    </ul>
  </nav>
</template>

<script>
export default {
  name: 'Navbar',
}
</script>
