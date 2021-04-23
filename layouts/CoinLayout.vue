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
/* @screen md {
  body {
    background: url('/img/purple_blur.png') no-repeat;
    background-position-x: 120%;
    background-position-y: -20%;
    background-size: 80%;
  }
} */
body {
  background: url('/img/purple_blur.png') no-repeat;
  background-position-x: 20vw;
  background-position-y: -20vh;
  background-size: 100vw;
}
/* Animations */
.slide-enter-active {
  animation: slide-in 0.4s ease-in-out;
}
.slide-leave-active {
  animation: slide-out 0.4s ease-in-out;
}
@keyframes slide-in {
  0% {
    opacity: 0;
  }
  100% {
    opacity: 1;
  }
}

@keyframes slide-out {
  0% {
    opacity: 1;
  }
  100% {
    opacity: 0;
  }
}
</style>
