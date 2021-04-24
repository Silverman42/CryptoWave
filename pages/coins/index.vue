<template>
  <div class="flex justify-between flex-wrap flex-col-reverse md:flex-row">
    <div class="w-full md:w-8/12 mb-5">
      <div class="mb-10 flex items-center">
        <nuxt-link
          to="/"
          class="w-10 h-10 rounded-full flex justify-center items-center border border-gray-300 hover:border-purple-600 hover:text-purple-600"
        >
          <iconify :icon="chevronLeft" width="20" height="20" />
        </nuxt-link>
        <h1 class="text-xl ml-5 font-bold">Bitcoin</h1>
        <div class="ml-auto text-sm">
          <outline-button
            >Reload
            <span class="inline-block ml-2"
              ><iconify :icon="refresh" width="16" height="16" /></span
          ></outline-button>
        </div>
      </div>
      <div class="mb-5">
        <coin-header v-if="pageLoading == false" />
        <header-skeleton v-else />
      </div>
      <div class="md:hidden mb-5">
        <social-media-stats />
      </div>
      <div class="mb-5 flex text-xs justify-between items-center">
        <span>
          Top 75 markets for <span class="text-purple-600">Bitcoin</span>
        </span>
        <primary-button>
          Save Coin
          <span class="ml-2">
            <iconify :icon="bookmark" width="14" height="14" />
          </span>
        </primary-button>
      </div>
      <div>
        <template v-if="listLoading == false">
          <coin-market
            v-for="(market, index) in 10"
            :key="index"
            :delay="`0.${index}`"
          />
        </template>
        <template v-else>
          <item-skeleton v-for="(market, index) in 10" :key="index" />
        </template>
      </div>
    </div>
    <div class="w-full md:w-3/12 hidden md:block">
      <social-media-stats v-if="pageLoading == false" />
      <social-skeleton v-else />
    </div>
  </div>
</template>

<script>
import chevronLeft from '@iconify/icons-feather/chevron-left'
import refresh from '@iconify/icons-feather/refresh-cw'
import bookmark from '@iconify/icons-feather/bookmark'
import Iconify from '~/components/Iconify.vue'
export default {
  components: { Iconify },
  layout: 'CoinLayout',
  transition: {
    name: 'fade',
    mode: 'in-out',
  },
  data() {
    return {
      chevronLeft,
      refresh,
      bookmark,
      pageLoading: true,
      listLoading: true,
    }
  },
  mounted() {
    this.loadCoins()
  },
  methods: {
    loadCoins() {
      setTimeout(() => {
        this.pageLoading = false
        this.listLoading = false
      }, 2000)
    },
  },
}
</script>

<style></style>
