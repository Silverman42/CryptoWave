<template>
  <div>
    <navbar>
      <li class="md:mr-10">
        <nuxt-link
          to="/"
          class="text-xs md:text-sm hover:text-purple-700 text-gray-800"
          >Home</nuxt-link
        >
      </li>
      <li class="md:mr-10">
        <nuxt-link
          to="/exchanges"
          class="text-xs md:text-sm hover:text-purple-700 text-gray-800"
          >Exchanges</nuxt-link
        >
      </li>
      <li>
        <nuxt-link
          to="saved"
          class="text-xs md:text-sm hover:text-purple-700 text-gray-800"
          >Saved</nuxt-link
        >
      </li>
    </navbar>
    <div class="max-w-6xl mx-auto p-4 pb-16">
      <Nuxt />
    </div>
  </div>
</template>

<script>
export default {
  name: 'CoinLayout',
}
</script>

<style></style>
