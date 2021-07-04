<template>
  <main v-if="!loading">
    <CountrySelect @get-country="getCountryData" :countries="countries" />
    <button
      @click="clearCountryData()"
      v-if="stats.Country"
      class="bg-gray-700 text-white rounded p-3 mt-5 focus:outline-none hover:bg-gray-600 "
    >
      <i class="far fa-times-circle"></i>
      Clear Country
    </button>
    <DataTitle :text="title" :dataDate="dataDate" />
    <DataBox :stats="stats" />
  </main>
  <main class="flex flex-col algin-center justify-center text-center" v-else>
    <div class="text-gray-500 text-3xl mt-10 mb-6">
      Fetching Data
    </div>
    <img :src="loadingImage" class="w-24 m-auto" alt="loading_img" />
  </main>
</template>

<script>
import DataTitle from '@/components/DataTitle';
import DataBox from '@/components/DataBox';
import CountrySelect from '@/components/CountrySelect';

export default {
  name: 'Home',
  //state
  data() {
    return {
      loading: true,
      title: 'Global',
      dataDate: '',
      stats: {},
      countries: [],
      loadingImage: require('../assets/hourglass.gif'),
    };
  },
  components: {
    DataTitle,
    DataBox,
    CountrySelect,
  },
  methods: {
    async fetchCovidData() {
      const res = await fetch('https://api.covid19api.com/summary');
      const data = await res.json();
      console.log(data);
      return data;
    },

    getCountryData(country) {
      this.stats = country;
      this.title = country.Country;
    },
    async clearCountryData() {
      this.loading = true;
      const data = await this.fetchCovidData();
      this.title = 'Global';
      this.stats = data.Global;
      this.loading = false;
    },
  },
  //life cycle methods
  async created() {
    const data = await this.fetchCovidData();

    this.dataDate = data.Date;
    this.stats = data.Global;
    this.countries = data.Countries;
    this.loading = false;
  },
};
</script>
