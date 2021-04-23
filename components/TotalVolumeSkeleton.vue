<template>
  <div class="rounded-3xl bg-white border border-gray-300 shadow-xl px-5 py-10">
    <div class="flex flex-col items-center mb-6">
      <span
        class="w-10 mb-3 flex justify-center text-yellow-400 items-center h-10 rounded-xl bg-yellow-200"
      >
        <iconify :icon="briefCase" width="28" height="28" />
      </span>
      <div class="p-2 w-5/12 my-4 animate-pulse rounded-full bg-gray-300"></div>
    </div>
    <div class="flex justify-between items-center mb-6">
      <div class="p-2 w-20 my-4 animate-pulse rounded-full bg-gray-300"></div>
      <div class="p-2 w-20 my-4 animate-pulse rounded-full bg-gray-300"></div>
    </div>
    <div class="flex justify-between items-center mb-6">
      <div class="p-2 w-20 my-4 animate-pulse rounded-full bg-gray-300"></div>
      <div class="p-2 w-20 my-4 animate-pulse rounded-full bg-gray-300"></div>
    </div>
  </div>
</template>

<script>
import briefCase from '@iconify/icons-feather/briefcase'
export default {
  data() {
    return {
      briefCase,
    }
  },
}
</script>

<style></style>
