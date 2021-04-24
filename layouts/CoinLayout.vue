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
body {
  background: url('/img/purple_blur.png') no-repeat;
  background-position-x: 20vw;
  background-position-y: -20vh;
  background-size: 100vw;
  overflow-x: hidden;
}

/* Animations */
.bounce-up {
  animation: bounceUp 0.3s ease-in forwards;
  animation-iteration-count: 1;
}
.fade-enter-active {
  animation: fade 0.2s ease-in-out;
}
.fade-leave-active {
  animation: fade 0.2s ease-in-out reverse;
}
.slide-enter-active {
  animation: slide 0.2s ease-in-out;
}
.slide-leave-active {
  animation: slide 0.2s ease-in-out reverse;
}
@keyframes fade {
  0% {
    opacity: 0;
  }
  100% {
    opacity: 1;
  }
}

@keyframes bounceUp {
  0% {
    opacity: 0;
    transform: translateY(-20px);
  }
  50% {
    opacity: 1;
    transform: translateY(20px);
  }
  100% {
    transform: translateY(0px);
  }
}

@keyframes slide {
  0% {
    opacity: 0;
    transform: translateX(20%);
  }
  100% {
    opacity: 1;
    transform: translateX(0%);
  }
}
</style>
