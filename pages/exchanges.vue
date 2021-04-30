<template>
  <div>
    <div class="flex mb-10 justify-between items-center mb-10">
      <h1 class="text-xl lg:text-2xl font-bold">Exchanges</h1>
      <div class="text-xs">
        <primary-button
          :disabled="loadingList"
          @clickButton="refreshExchangelist"
          >Refresh
          <span class="ml-2"
            ><iconify :icon="refresh" width="14" height="14" /></span
        ></primary-button>
      </div>
    </div>
    <transition name="fade">
      <modal-backdrop
        v-if="modalOpen === true"
        @closeModal="toggleModal(false)"
      />
    </transition>
    <transition name="slide">
      <modal
        v-if="modalOpen === true"
        :isopen="modalOpen"
        @update:isopen="toggleModal(false)"
      >
        {{ selectedData.name }}
        <div slot="body">
          <div class="mb-5">
            <exchange-header
              v-if="loadingExchangeData === false"
              :data="selectedData"
            />
            <header-skeleton v-else />
          </div>
          <div class="mb-5 text-sm">
            Top pairs for
            <span class="capitalize text-purple-500">{{
              selectedData.name
            }}</span>
          </div>
          <div class="grid grid-cols-2 lg:grid-cols-4 col-gap-6 row-gap-6">
            <template v-if="loadingPairList === false">
              <exchange-pair
                v-for="(pair, index) in selectedExchangePairs"
                :key="index"
                :delay="`0.${index}`"
                :data="pair"
              />
            </template>
            <template v-else>
              <exchange-pair-skeleton
                v-for="(item, index) in 10"
                :key="index"
              />
            </template>
          </div>
        </div>
      </modal>
    </transition>
    <section
      class="w-full mb-5 grid grid-cols-1 lg:grid-cols-4 col-gap-6 row-gap-6"
    >
      <template v-if="loadingList == false">
        <markets
          v-for="(market, key, index) in exchanges"
          :key="index"
          :delay="`0.${index}`"
          :data="market"
          @viewMarket="viewMarketInfo($event)"
        />
      </template>
      <template v-else>
        <market-skeleton v-for="(market, index) in 10" :key="index" />
      </template>
    </section>
  </div>
</template>

<script>
import refresh from '@iconify/icons-feather/refresh-cw'
export default {
  layout: 'CoinLayout',
  async fetch() {
    await this.loadExchanges()
  },
  transition: {
    name: 'fade',
    mode: 'in-out',
  },
  data() {
    return {
      modalOpen: false,
      loadingList: true,
      loadingPairList: true,
      loadingExchangeData: true,
      refresh,
      exchanges: {},
      selectedExchangePairs: [],
      selectedData: {
        name: '',
        name_id: '',
        url: '',
        country: '',
        date_live: '0000-00-00 00:00:00',
        volume_usd: '',
        fiat: '0',
        volume_usd_adj: '',
        pairs: '',
        usdt: '',
        date_added: '0000-00-00 00:00:00',
        id: '0',
      },
    }
  },
  methods: {
    viewMarketInfo(marketData) {
      this.modalOpen = true
      this.loadExchangePairs(marketData.id)
      this.selectedData = marketData
    },
    toggleModal(modalState) {
      this.modalOpen = modalState
      modalState === false
        ? this.changeExchangeInfoState(true)
        : this.changeExchangeInfoState(false)
    },
    changeExchangeInfoState(state) {
      this.loadingPairList = state
      this.loadingExchangeData = state
    },
    async loadExchangePairs(exchangeId) {
      await fetch(`https://api.coinlore.net/api/exchange/?id=${exchangeId}`)
        .then((res) => res.json())
        .then((res) => {
          this.selectedExchangePairs = res.pairs
          this.changeExchangeInfoState(false)
        })
    },
    async loadExchanges() {
      await fetch('https://api.coinlore.net/api/exchanges/')
        .then((res) => res.json())
        .then((res) => {
          this.exchanges = res
          this.loadingList = false
        })
    },
    refreshExchangelist() {
      this.loadingList = true
      this.loadExchanges()
    },
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
