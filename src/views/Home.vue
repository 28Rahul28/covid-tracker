<template>
  <main v-if="!loading">
    <datatitle :text="title" :datadate = "datadate"/>
    <databoxes :data="stats"/>
    <selector @get-country = "changedata" :options = "countries" :total= "global" />

  </main>
  <main class="flex flex-col align-center justify-center text-center" v-else>
    <div class="text-gray-500 text-3xl mt-10 mb-6">Fetching Data</div>
    <img :src="loadingimage" class="w-100 m-auto" alt="">
    
  </main>
</template>

<script>
// @ is an alias to /src
import datatitle from '@/components/datatitle'
import selector from '@/components/selector'
import Databoxes from '@/components/databoxes'


export default {
  name: 'Home',
  components: {
    datatitle,
    selector,
    Databoxes,
    
  },
  data(){
    return {
      loading:true,
      title: 'global',
      datadate: '',
      stats :{},
      global:{},
      countries: [],
      loadingimage: require('../assets/loading.gif')
    }
  },
  methods: {
    async fetchcoviddata(){
      const res = await fetch('https://api.covid19api.com/summary')
      const data = await res.json()
      return data
    },
    changedata(country){
      this.stats = country
      this.title = country.Country ? country.Country:'Global'
    }
  },
  async created(){
    const data = await this.fetchcoviddata()
    this.datadate = data.Date
    this.stats = data.Global
    this.global = data.Global
    this.countries = data.Countries
    this.loading = false
  }
}
</script>
