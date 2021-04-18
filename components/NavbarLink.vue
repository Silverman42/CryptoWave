<template>
  <li>
    <nuxt-link :to="to" class="navlink">
      <span>
        <slot name="linkIcon" />
      </span>
      <span>
        <slot />
      </span>
    </nuxt-link>
  </li>
</template>

<script>
export default {
  props: {
    to: {
      type: [String, Object],
      default: '',
    },
  },
}
</script>

<style scoped>
.navlink {
  @apply text-xs text-gray-800 inline-flex flex-col items-center;
}
.navlink:hover {
  @apply text-purple-700;
}
.navlink > span:first-child {
  @apply inline-block mb-2;
}

@screen md {
  .navlink {
    @apply text-sm ml-10;
  }
  .navlink > span:first-child {
    @apply hidden;
  }
}
</style>
