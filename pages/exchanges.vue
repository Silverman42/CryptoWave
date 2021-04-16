<template>
  <div>
    <h1 class="mb-5 text-xl lg:text-2xl font-bold">Exchanges</h1>
    <modal-backdrop v-if="modalOpen === true" />
    <modal v-if="modalOpen === true">
      <div slot="body">
        <div class="mb-5">
          <exchange-header />
        </div>
        <div class="grid grid-cols-2 lg:grid-cols-4 col-gap-6 row-gap-6">
          <exchange-pair v-for="(item, index) in 10" :key="index" />
        </div>
      </div>
    </modal>
    <section
      class="w-full mb-5 grid grid-cols-1 lg:grid-cols-4 col-gap-6 row-gap-6"
    >
      <markets v-for="(market, index) in 10" :key="index" />
    </section>
  </div>
</template>

<script>
export default {
  layout: 'CoinLayout',
  data() {
    return {
      modalOpen: true,
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
