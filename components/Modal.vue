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
        >
          B
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
export default {
  mounted() {
    const body = document.querySelector('body')
    body.classList.add('overflow-y-hidden')
  },
}
</script>

<style></style>
