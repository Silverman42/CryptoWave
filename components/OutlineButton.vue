<template>
  <button
    class="border py-2 px-5 capitalize flex items-center rounded-full hover:border-purple-800 hover:text-purple-800"
  >
    <slot>Button</slot>
  </button>
</template>

<script>
export default {
  name: 'Buttons',
}
</script>

<style></style>
