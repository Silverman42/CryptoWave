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
        <coin-item
          v-for="(item, index) in 10"
          :key="index"
          :to="{ path: `/coins`, query: { id: index } }"
        />
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
          <market-cap-widget />
        </div>
        <div class="mb-5">
          <total-volume-widget />
        </div>
        <div class="mb-5">
          <dominance-widget />
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
  data() {
    return {
      icon: {
        refresh,
        chevronDown,
        filter,
      },
    }
  },
}
</script>

<style>
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
  font-family: 'Quicksand', 'Source Sans Pro', -apple-system, BlinkMacSystemFont,
    'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}
</style>
