<template>
  <div class="block border bg-purple-700 w-full p-5 rounded-2xl shadow-xl">
    <div class="flex justify-between items-center">
      <div class="w-5/12 mr-2 flex">
        <img
          class="w-10 h-10 rounded-full p-1 bg-white mr-3"
          :src="`https://www.coinlore.com/img/exchanges/${data.name_id}.png`"
          :alt="data.name"
          @error="setDefaultImage($event)"
        />
        <div>
          <h6 class="text-white text-sm font-bold mb-1 capitalize">
            {{ data.name }}
          </h6>
          <p class="text-xs text-purple-300 capitalize">{{ data.country }}</p>
        </div>
      </div>
      <div class="w-6/12 text-right">
        <a
          :href="data.url"
          target="_blank"
          class="border text-sm py-3 px-6 capitalize inline-flex items-center rounded-full whitespace-no-wrap border-purple-400 text-purple-300 hover:border-white hover:text-white"
        >
          <span class="mr-2">Visit Website</span>
          <span>></span>
        </a>
      </div>
    </div>
    <div class="my-5">
      <span class="block text-lg text-yellow-300 font-bold">
        ${{ data.volume_usd | formatNumber }}
      </span>
      <span class="text-xs text-purple-300">Volume</span>
    </div>
    <div class="flex my-5">
      <div class="flex-grow w-full text-white flex overflow-x-auto">
        <div class="mr-5">
          <p class="text-xs font-bold whitespace-nowrap">
            ${{ data.volume_usd_adj | formatNumber }}
          </p>
          <span class="text-xs text-purple-300">Adj. Volume</span>
        </div>
        <div class="mr-5">
          <p class="text-xs font-bold whitespace-no-wrap">
            {{ data.pairs | formatNumber('int') }}
          </p>
          <span class="text-xs text-purple-300">Pairs</span>
        </div>
        <div class="mr-5">
          <p class="text-xs font-bold whitespace-no-wrap">
            {{ data.usdt === '1' ? 'True' : 'False' }}
          </p>
          <span class="text-xs text-purple-300">USDT</span>
        </div>
        <div class="mr-5">
          <p class="text-xs font-bold whitespace-no-wrap">
            {{ data.fiat === '1' ? 'True' : 'False' }}
          </p>
          <span class="text-xs text-purple-300">Fiat</span>
        </div>
        <div class="mr-5">
          <p class="text-xs font-bold whitespace-no-wrap">
            {{ data.date_added | formatDate }}
          </p>
          <span class="text-xs text-purple-300">Founded</span>
        </div>
        <div class="mr-5">
          <p class="text-xs font-bold whitespace-no-wrap">
            {{ data.date_live | formatDate }}
          </p>
          <span class="text-xs text-purple-300">Date Live</span>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'ExchangeHeader',
  filters: {
    formatNumber(number, parseType = 'float') {
      const parsedNumber =
        parseType === 'int' ? parseInt(number) : parseFloat(number)
      const formatted = new Intl.NumberFormat('en-US', {
        style: 'decimal',
        maximumFractionDigits: 2,
      }).format(parsedNumber)
      return formatted
    },
    formatDate(date) {
      if (date === '0000-00-00 00:00:00') {
        return 'Unknown Date'
      }
      const newDate = new Date(date)
      return new Intl.DateTimeFormat('en-GB', {
        year: 'numeric',
        month: 'short',
        day: 'numeric',
      }).format(newDate)
    },
  },
  props: {
    data: {
      type: Object,
      default() {
        return {
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
          id: '',
        }
      },
    },
  },
  methods: {
    setDefaultImage(event) {
      event.target.onerror = null
      event.target.src = './img/coin.svg'
    },
  },
}
</script>

<style></style>
