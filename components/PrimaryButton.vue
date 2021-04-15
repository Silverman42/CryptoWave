<template>
  <button
    class="border py-3 px-6 capitalize flex items-center rounded-full bg-purple-600 text-white hover:bg-purple-800"
  >
    <slot> Button </slot>
  </button>
</template>

<script>
export default {
  name: 'PrimaryButton',
}
</script>

<style></style>
