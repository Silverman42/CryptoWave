<template>
  <iconify-icon :width="width" :height="height" :icon="icon" />
</template>

<script>
import IconifyIcon from '@iconify/vue'
export default {
  components: {
    IconifyIcon,
  },
  props: {
    width: {
      type: [String, Number],
      default: 10,
    },
    height: {
      type: [String, Number],
      default: 10,
    },
    icon: {
      type: [String, Object],
      default() {
        return {}
      },
    },
  },
}
</script>
