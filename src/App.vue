<template>
  <h1 class="text-3xl font-bold">
    {{ title }}
  </h1>

  <div v-if="true" class="text-3xl p-6">
    {{ clickedCountry.common}}
  </div>
  <div class="grid sm:grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-4 px-8 py-4 " >
  <div @click="btnClick(country.name)" class="p-8 bg-cyan-600 border rounded-lg" v-for="country in countries" :key="country.index">
      <h2 class="text-2xl">{{ country.name.common }}</h2>
      <p>{{ country.region }}</p>
      <p>{{  }}</p>
      <img class="w-full h-48 object-cover" :src="country.flags.png" alt="image">
      <button  class="mt-5 rounded-md bg-cyan-500 hover:bg-cyan-700 ">Details</button>
    </div>    
    
  </div>

</template>

<script>
export default{
  data(){
    return{
      title: 'My First Vue app',
      countries:[],
      clickedCountry: {},
      showDetail: false

    }
  },
  mounted(){
    this.getCountries();
  },
  methods:{
    getCountries(){
    fetch('https://restcountries.com/v3.1/all')
    .then(res => res.json())
    .then(data => this.countries = data)
    .catch(err => console.log(err.message))
  },

  btnClick(e){
    this.clickedCountry = e;
    console.log(this.clickedCountry.common)
    this.showDetail = !this.showDetail
    console.log(this.showDetail)
  }

        // getCountries(){
        //   let url = 'https://restcountries.com/v3.1/all';
        //   axios.get(url).then(res =>{
        //     this.countries = res.data
        //     console.log(this.countries)
        //   })
        // }
  }
}
</script>

<style scoped>

</style>
