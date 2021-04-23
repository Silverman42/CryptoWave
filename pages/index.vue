<template>
  <div>
    <h1 class="mb-10 text-xl lg:text-2xl w-full font-bold">Home</h1>
    <section
      class="flex justify-between flex-wrap flex-col-reverse md:flex-row"
    >
      <div class="w-full md:w-8/12 mb-5">
        <div class="mb-20 flex justify-end items-center text-xs">
          <div class="mr-2">
            <outline-button
              >Filter
              <span class="ml-2"
                ><iconify :icon="icon.filter" width="14" height="14" /></span
            ></outline-button>
          </div>
          <div class="mr-2">
            <outline-button
              >Sort-By
              <span class="ml-2"
                ><iconify
                  :icon="icon.chevronDown"
                  width="14"
                  height="14" /></span
            ></outline-button>
          </div>
          <div>
            <outline-button
              >Refresh
              <span class="ml-2"
                ><iconify :icon="icon.refresh" width="14" height="14" /></span
            ></outline-button>
          </div>
        </div>
        <template v-if="listLoading == false">
          <coin-item
            v-for="(item, index) in 10"
            :key="index"
            :to="{ path: `/coins`, query: { id: index } }"
          />
        </template>
        <template v-else>
          <item-skeleton v-for="(item, index) in 10" :key="index" />
        </template>
        <div class="pt-5 text-sm flex justify-center">
          <primary-button>
            Load more
            <span class="ml-2"
              ><iconify :icon="icon.chevronDown" width="14" height="14"
            /></span>
          </primary-button>
        </div>
      </div>
      <div class="w-full md:w-3/12">
        <div class="mb-5">
          <market-cap-widget v-if="pageLoading == false" />
          <market-cap-skeleton v-else />
        </div>
        <div class="mb-5">
          <total-volume-widget v-if="pageLoading == false" />
          <total-volume-skeleton v-else />
        </div>
        <div class="mb-5">
          <dominance-widget v-if="pageLoading == false" />
          <dominance-skeleton v-else />
        </div>
      </div>
    </section>
  </div>
</template>

<script>
import refresh from '@iconify/icons-feather/refresh-cw'
import chevronDown from '@iconify/icons-feather/chevron-down'
import filter from '@iconify/icons-feather/filter'
export default {
  layout: 'CoinLayout',
  transition: {
    name: 'slide',
    mode: 'in-out',
  },
  data() {
    return {
      icon: {
        refresh,
        chevronDown,
        filter,
      },
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
      }, 8000)
    },
  },
}
</script>

<style></style>
