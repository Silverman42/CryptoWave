<template>
  <div
    class="fixed top-0 right-0 bottom-0 h-screen w-screen opacity-50 bg-black z-40"
    @click="closeModal"
  ></div>
</template>

<script>
export default {
  methods: {
    closeModal() {
      this.$emit('closeModal')
    },
  },
}
</script>

<style></style>
