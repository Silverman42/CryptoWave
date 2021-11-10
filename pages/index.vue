<template>
  <div>
    <div class="flex justify-center items-center mb-10">
      <h1 class="text-xl lg:text-2xl w-full font-bold">Home</h1>
      <div class="text-xs">
        <primary-button
          :disabled="disableFilterButton"
          @clickButton="refreshPage"
          >Refresh
          <span class="ml-2"
            ><iconify :icon="icon.refresh" width="14" height="14" /></span
        ></primary-button>
      </div>
    </div>
    <section
      class="flex justify-between flex-wrap flex-col-reverse md:flex-row"
    >
      <div class="w-full md:w-8/12 mb-5">
        <div class="mb-20 flex justify-end items-center text-xs">
          <div class="mr-2">
            <outline-button :disabled="disableFilterButton"
              >Filter
              <span class="ml-2"
                ><iconify :icon="icon.filter" width="14" height="14" /></span
            ></outline-button>
          </div>
          <div class="mr-2">
            <outline-button :disabled="disableFilterButton"
              >Sort-By
              <span class="ml-2"
                ><iconify
                  :icon="icon.chevronDown"
                  width="14"
                  height="14" /></span
            ></outline-button>
          </div>
        </div>
        <template v-if="pageLoading == false">
          <coin-item
            v-for="(coin, index) in coins"
            :key="`${index}cl`"
            :delay="`0.${index}`"
            :to="{ path: `/coins`, query: { id: coin.id || 0 } }"
            :data="coin"
          />
        </template>
        <template v-if="listLoading == true">
          <item-skeleton v-for="(item, index) in 10" :key="index" />
        </template>
        <div class="pt-5 text-sm flex justify-center">
          <primary-button
            :disabled="disableMoreButton"
            @clickButton="loadMoreCoins"
          >
            Load more
            <span class="ml-2"
              ><iconify :icon="icon.chevronDown" width="14" height="14"
            /></span>
          </primary-button>
        </div>
      </div>
      <div class="w-full md:w-3/12">
        <div class="mb-5">
          <market-cap-widget
            v-if="pageLoading == false"
            :market-cap="marketCap"
          />
          <market-cap-skeleton v-else />
        </div>
        <div class="mb-5">
          <total-volume-widget
            v-if="pageLoading == false"
            :volume="{ ...volume }"
          />
          <total-volume-skeleton v-else />
        </div>
        <div class="mb-5">
          <dominance-widget
            v-if="pageLoading == false"
            :dominance="{ ...dominance }"
          />
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
    name: 'fade',
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
      coins: [],
      listData: {
        start: 0,
        length: 0,
      },
      marketCap: 0,
      dominance: {
        eth_d: 0,
        btc_d: 0,
      },
      volume: {
        mcap_ath: 0,
        volume_ath: 0,
        coins_count: 0,
        active_markets: 0,
        total_volume: 0,
      },
    }
  },
  computed: {
    disableMoreButton() {
      if (
        this.listData.length === 0 ||
        this.listLoading === true ||
        this.pageLoading === true
      ) {
        return true
      }
      return false
    },
    disableFilterButton() {
      if (this.listLoading === true || this.pageLoading === true) {
        return true
      }
      return false
    },
  },
  mounted() {
    this.loadCoins()
    this.loadWidgets()
  },
  methods: {
    setListData({ start = 0, limit = 100, data = [] }) {
      this.$set(this.listData, 'start', start + limit)
      this.$set(this.listData, 'length', data.length)
    },
    refreshList(data = []) {
      this.coins = data
    },
    appendList(data = []) {
      this.coins = [...this.coins, ...data]
    },
    loadCoins({ start = 0, limit = 100, refresh = false } = {}) {
      fetch(
        `https://api.coinlore.net/api/tickers/?start=${start}&limit=${limit}`
      )
        .then((res) => res.json())
        .then((res) => {
          refresh === true
            ? this.refreshList(res.data)
            : this.appendList(res.data)
          this.setListData({ data: res.data, start, limit })
          return res
        })
        .then((res) => {
          this.listLoading = false
        })
    },
    loadMoreCoins() {
      this.listLoading = true
      this.loadCoins({ start: this.listData.start })
    },
    loadWidgets() {
      fetch('https://api.coinlore.net/api/global/')
        .then((res) => res.json())
        .then((res) => {
          this.marketCap = parseFloat(res[0].mcap_ath)
          this.dominance = {
            eth_d: res[0].eth_d,
            btc_d: res[0].btc_d,
          }
          this.volume = res[0]
          this.pageLoading = false
        })
    },
    refreshPage() {
      this.pageLoading = true
      this.listLoading = true
      this.loadCoins({ refresh: true })
      this.loadWidgets()
    },
  },

  head: {
    title: 'CryptoWave',
    meta: [
      {
        hid: 'description',
        name: 'description',
        content:
          'A simple web application for getting realtime data about cryptocurrencies',
      },
      {
        property: 'twitter:url',
        content: 'http://crypto-wave.netlify.app',
      },
      {
        property: 'twitter:title',
        content: 'CryptoWave',
      },
      {
        property: 'twitter:description',
        content:
          'A simple web application for getting realtime data about cryptocurrencies',
      },
      {
        property: 'og:url',
        content: 'http://crypto-wave.netlify.app',
      },
      {
        property: 'og:title',
        content: 'CryptoWave',
      },
      {
        property: 'og:description',
        content:
          'A simple web application for getting realtime data about cryptocurrencies',
      },
    ],
  },
}
</script>

<style></style>
