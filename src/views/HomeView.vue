<template>
  <Input @name-from-input="setName" />
  <CountryBoxes :countriesInfo="countriesInfo" />
  <main v-if="loading" class="text-center">
    <img :src="loadingImage" class="w-24 m-auto" alt="">
  </main>
  <main v-if="!loading & empty" class="text-center text-4xl font-bold mt-12">Not Found</main>
</template>

<script>
import Input from '@/components/Input.vue';
import CountryBoxes from '@/components/CountryBoxes.vue';

export default {
    name: "HomeView",
    components: { Input, CountryBoxes },
    data() {
      return {
        name: "",
        loading: false,
        empty: false,
        countriesInfo: [],
        loadingImage: require('../assets/hourglass.gif')
      }
    },
    methods: {
      setName({name, loading}) {
        this.name = name;
        this.loading = loading;
        this.empty = false;
      },
      async getCountry() {
        //clear all countries info first before next fetch
        this.countriesInfo = [];

        const res = await fetch(`https://api.nationalize.io/?name=${this.name}`);
        const data = await res.json();

        let countries = data.country; 

        countries.forEach(element => {
          //give country id to the next func
          this.getCountryInfo(element.country_id, element.probability)
        });

        setTimeout(()=>{
          this.loading = false;
          this.empty = this.countriesInfo.length === 0;
        } ,1000)
      },
      async getCountryInfo(id, prob){
        const res = await fetch(`https://restcountries.com/v2/alpha/${id}`);
        const data = await res.json();
        
        this.countriesInfo.push({
          'name': data.name,
          'img': data.flags.svg,
          'probability': prob
        })
      }
    },
    watch: {
      name(newName, oldName) {
        if (newName !== oldName)
          this.getCountry()
    },
  }
}
</script>
