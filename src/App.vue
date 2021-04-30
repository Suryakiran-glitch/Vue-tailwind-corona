<template>
<Header/>
  <div class="container">
    <main v-if="!loading">
      <DataTitle :title="title" :dataDate="dataDate"  />
      <DataCard :status="status" />
      <CountrySelect @get-country="getCountryData" :countries="countries" />
      <button @click="clearCountry()" v-if="stats.Country" class="bg-green-700 rounded white-text mt-10 p-3 focus:outline-none hover:bg-green-400">Clear</button>
    </main>
    <main v-else class="flex flex-col align-center justify-center text-center">
      <h3 class="text-3xl text-grey-400 mb-8 mt-8">Loading Please Wait !!!</h3>
      <img :src="loadingImage" alt="Img" class="w-24 m-auto" />
    </main>
  </div>
</template>

<script>
import Header from './components/Header'
import DataTitle from './components/DataTitle'
import DataCard from "./components/DataCard"
import CountrySelect from "./components/CountrySelect"

export default {
  name: 'App',
  components : {
    Header,
    DataTitle,
    DataCard,
    CountrySelect
},
data() {
  return{
    loading : true,
    title : 'Global',
    dataDate : '',
    status : {},
    countries : [],
    loadingImage : require('./assets/Hourglass.gif')
  }
},
methods : {
  async getCovidData() {
    const res = await fetch("https://api.covid19api.com/summary")
    const data = await res.json()
    return data
  },
  getCountryData(country) {
    this.title=country
    this.status = country.Country
  },
  async clearCountry() {
    this.loading=true
    const res = await fetch("https://api.covid19api.com/summary")
    const data = await res.json()
    this.title="Global"
    this.status = data.Global
    this.loading = false
  }
},
async created () {
  const data = await this.getCovidData()
  this.dataDate = data.Date
  this.status = data.Global
  this.countries = data.Countries
  this.loading = false
}
}
</script>


