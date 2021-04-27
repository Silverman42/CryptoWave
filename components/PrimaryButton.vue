<template>
  <button class="button" :disabled="disabled" @click="clickButton">
    <slot> Button </slot>
  </button>
</template>

<script>
export default {
  name: 'PrimaryButton',
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
  @apply border py-3 px-6 capitalize flex items-center rounded-full bg-purple-600 text-white;
}
.button:hover {
  @apply bg-purple-800;
}
.button:disabled {
  @apply opacity-50;
  cursor: not-allowed;
}
</style>
