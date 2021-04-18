<template>
  <aside
    class="h-screen bottom-0 top-0 right-0 fixed z-40 bg-white block w-screen md:w-3/4 overflow-y-auto"
  >
    <div class="max-w-4xl mx-auto px-5 pb-8">
      <header
        class="py-5 flex sticky top-0 bg-white z-30 items-center border-b mb-5"
      >
        <button
          class="w-10 h-10 rounded-full flex justify-center items-center border border-gray-300 hover:border-purple-600 hover:text-purple-600"
          @click="closeModal"
        >
          <iconify :icon="chevronLeft" width="20" height="20" />
        </button>
        <p class="text-xl ml-5 font-bold"><slot>Header</slot></p>
      </header>
      <section>
        <slot name="body" />
      </section>
    </div>
  </aside>
</template>

<script>
import chevronLeft from '@iconify/icons-feather/chevron-left'
export default {
  props: {
    isopen: {
      type: Boolean,
      default: false,
    },
  },
  data() {
    return {
      body: document.querySelector('body'),
      chevronLeft,
    }
  },
  mounted() {
    const vm = this
    vm.body.classList.add('overflow-y-hidden')
    window.addEventListener('keyup', (event) => {
      event.preventDefault()
      if (event.keyCode === 27) vm.closeModal()
    })
  },
  destroyed() {
    this.body.classList.remove('overflow-y-hidden')
  },
  methods: {
    closeModal() {
      return this.$emit('update:isopen', false)
    },
  },
}
</script>

<style></style>
