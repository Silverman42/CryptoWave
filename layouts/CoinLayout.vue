<template>
  <div class="font-serif">
    <navbar>
      <navbar-link to="/"
        ><template slot="linkIcon"
          ><iconify :icon="icon.home" width="18" height="18"
        /></template>
        Home
      </navbar-link>
      <navbar-link to="/exchanges">
        <template slot="linkIcon"
          ><iconify :icon="icon.barChart" width="18" height="18"
        /></template>
        Exchanges
      </navbar-link>
      <navbar-link to="/saved">
        <template slot="linkIcon"
          ><iconify :icon="icon.saved" width="18" height="18"
        /></template>
        Saved
      </navbar-link>
    </navbar>
    <div class="max-w-6xl mx-auto p-4 pb-16">
      <Nuxt />
    </div>
  </div>
</template>

<script>
import barChart from '@iconify/icons-feather/bar-chart-2'
import saved from '@iconify/icons-feather/bookmark'
import home from '@iconify/icons-feather/home'
export default {
  name: 'CoinLayout',
  data() {
    return {
      icon: {
        barChart,
        saved,
        home,
      },
    }
  },
}
</script>

<style>
.font-serif {
  font-family: 'Open Sans', sans-serif;
}
</style>
