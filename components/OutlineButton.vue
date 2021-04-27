<template>
  <button class="button" :disabled="disabled" @click="clickButton">
    <slot>Button</slot>
  </button>
</template>

<script>
export default {
  name: 'Buttons',
  props: {
    disabled: {
      type: Boolean,
      default: false,
    },
  },
  methods: {
    clickButton() {
      this.$emit('clickButton')
    },
  },
}
</script>

<style scoped>
.button {
  @apply border border-gray-400 py-2 px-5 capitalize flex items-center rounded-full;
}
.button:hover {
  @apply border-purple-800 text-purple-800;
}
.button:disabled {
  @apply opacity-50;
  cursor: not-allowed;
}
</style>
