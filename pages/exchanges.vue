<template>
  <div>
    <h1 class="mb-10 text-xl lg:text-2xl font-bold">Exchanges</h1>
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
        Binance
        <div slot="body">
          <div class="mb-5">
            <exchange-header v-if="loadingExchangeData === false" />
            <header-skeleton v-else />
          </div>
          <div class="grid grid-cols-2 lg:grid-cols-4 col-gap-6 row-gap-6">
            <template v-if="loadingPairList === false">
              <exchange-pair
                v-for="(item, index) in 10"
                :key="index"
                :delay="`0.${index}`"
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
          v-for="(market, index) in 10"
          :key="index"
          :delay="`0.${index}`"
          @viewMarket="viewMarketInfo(index)"
        />
      </template>
      <template v-else>
        <market-skeleton v-for="(market, index) in 10" :key="index" />
      </template>
    </section>
  </div>
</template>

<script>
export default {
  layout: 'CoinLayout',
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
    }
  },
  mounted() {
    this.loadList()
  },
  methods: {
    viewMarketInfo(marketId) {
      this.modalOpen = true
      this.loadExchangePairs()
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
    loadExchangePairs() {
      setTimeout(() => {
        this.changeExchangeInfoState(false)
      }, 2000)
    },
    loadList() {
      setTimeout(() => {
        this.loadingList = false
      }, 2000)
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
