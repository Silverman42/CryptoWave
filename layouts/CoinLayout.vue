<template>
  <div class="font-serif">
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

<style>
@font-face {
  font-family: 'Circular Std Book';
  src: url('/font/860c3ec7bbc5da3e97233ccecafe512e.eot'); /* IE9*/
  src: url('/font/860c3ec7bbc5da3e97233ccecafe512e.eot?#iefix')
      format('embedded-opentype'),
    /* IE6-IE8 */ url('/font/860c3ec7bbc5da3e97233ccecafe512e.woff2')
      format('woff2'),
    /* chrome、firefox */ url('/font/860c3ec7bbc5da3e97233ccecafe512e.woff')
      format('woff'),
    /* chrome、firefox */ url('/font/860c3ec7bbc5da3e97233ccecafe512e.ttf')
      format('truetype'),
    /* chrome、firefox、opera、Safari, Android, iOS 4.2+*/
      url('/font/860c3ec7bbc5da3e97233ccecafe512e.svg#Circular Std Book')
      format('svg'); /* iOS 4.1- */
}
.font-serif {
  font-family: 'Circular Std Book', sans-serif;
}
</style>
