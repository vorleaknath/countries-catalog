<template>
  <div>
    <div v-for="(country, index) in countries" :key="index">
      <CountryCard @btn-click="getCountry" :country="country"/>
    </div>
    <teleport to="body">
        <div v-if="isClicked" v-for="countryInfo in countriesInfo" class="flex justify-center bg-black">
          <CountryModal :countryInfo="countryInfo" @btn-close="onClose()"/>
        </div>
    </teleport>
  </div>

</template>

<script>
import axios from 'axios'
import CountryCard from '../components/CountryCard.vue'
import CountryModal from './CountryModal.vue'

export default {
  name: "Catalogs",
  props: {
    countries: Array,
  },
  components: { 
    CountryCard, 
    CountryModal, 
  },
  data() {
    return {
      countriesInfo: [],
      isClicked: false,
    }
  },
  methods: {
    
    //  Fetch country by name
    async getCountry(name) {
      this.isClicked = !this.isClicked
      await axios
        .get(`https://restcountries.com/v3.1/name/${name}?fullText=true`)
        .then((response) => {
      this.countriesInfo = response.data
      })
      .catch((error) => {
        console.error(error)
      })
    },

    //Close Modal 
    onClose () {
       this.isClicked = !this.isClicked
    }
  }
}
</script>