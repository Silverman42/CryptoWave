<template>
  <!--  -->
  <div>
    <div class="mb-10 flex items-center">
      <nuxt-link
        to="/"
        class="w-10 h-10 rounded-full flex justify-center items-center border border-gray-300 hover:border-purple-600 hover:text-purple-600"
      >
        <iconify :icon="chevronLeft" width="20" height="20" />
      </nuxt-link>
      <h1 class="text-xl ml-5 font-bold">{{ coinData.name }}</h1>
      <div class="ml-auto text-sm">
        <outline-button :disabled="pageLoading" @clickButton="refreshData"
          >Reload
          <span class="inline-block ml-2"
            ><iconify :icon="refresh" width="16" height="16" /></span
        ></outline-button>
      </div>
    </div>
    <div class="flex justify-between flex-wrap flex-col-reverse md:flex-row">
      <div class="w-full md:w-8/12 mb-5">
        <div class="mb-5">
          <coin-header v-if="pageLoading == false" :data="{ ...coinData }" />
          <header-skeleton v-else />
        </div>
        <div class="md:hidden mb-5">
          <social-media-stats
            v-if="pageLoading == false"
            :reddit="{ ...socialStats.reddit }"
            :twitter="{ ...socialStats.twitter }"
          />
          <social-skeleton v-else />
        </div>
        <div class="mb-5 flex text-xs justify-between items-center">
          <span>
            Top 75 markets for
            <span class="text-purple-600 capitalize"> {{ coinData.name }}</span>
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
              v-for="(market, index) in coinMarkets"
              :key="index"
              :delay="`0.${index}`"
              :data="{ ...market }"
            />
          </template>
          <template v-else>
            <item-skeleton v-for="(market, index) in 10" :key="index" />
          </template>
        </div>
      </div>
      <div class="w-full md:w-3/12 hidden md:block">
        <social-media-stats
          v-if="socialStatsLoading == false"
          :reddit="{ ...socialStats.reddit }"
          :twitter="{ ...socialStats.twitter }"
        />
        <social-skeleton v-else />
      </div>
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
  async fetch() {
    await this.loadCoindata()
    await this.fetchSocialStats()
    await this.fetchMarkets()
  },
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
      socialStatsLoading: true,
      coinData: {
        symbol: 'BTC',
        name: 'Bitcoin',
        nameid: 'bitcoin',
        rank: 1,
        price_usd: '54729.21',
        percent_change_24h: '2.26',
        percent_change_1h: '0.15',
        percent_change_7d: '-3.22',
        market_cap_usd: '1021381176519.40',
        volume24: '78854052889.00',
        volume24_native: '1440803.89',
        csupply: '18662452.00',
        price_btc: '1.00',
        tsupply: '18662452',
        msupply: '21000000',
      },
      coinMarkets: [],
      socialStats: {
        reddit: {},
        twitter: {},
      },
    }
  },
  methods: {
    loadCoin() {
      setTimeout(() => {
        this.pageLoading = false
        this.listLoading = false
        this.socialStatsLoading = false
      }, 2000)
    },
    async loadCoindata() {
      await fetch(
        `https://api.coinlore.net/api/ticker/?id=${this.$route.query.id}`
      )
        .then((res) => res.json())
        .then((res) => {
          this.coinData = { ...res[0] }
          this.pageLoading = false
        })
    },
    async fetchSocialStats() {
      await fetch(
        `https://api.coinlore.net/api/coin/social_stats/?id=${this.$route.query.id}`
      )
        .then((res) => res.json())
        .then((res) => {
          this.socialStats.reddit = res.reddit
          this.socialStats.twitter = res.twitter
          this.socialStatsLoading = false
        })
    },
    async fetchMarkets() {
      await fetch(
        `https://api.coinlore.net/api/coin/markets/?id=${this.$route.query.id}`
      )
        .then((res) => res.json())
        .then((res) => {
          this.coinMarkets = res
          this.listLoading = false
        })
    },
    async refreshData() {
      this.pageLoading = true
      this.socialStatsLoading = true
      this.listLoading = true
      await this.loadCoindata()
      await this.fetchSocialStats()
      await this.fetchMarkets()
    },
  },
}
</script>

<style></style>
