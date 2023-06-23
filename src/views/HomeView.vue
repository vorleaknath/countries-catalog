<template>
  <div>
    <Header @btn-search="searchCountries" />
    <div class="flex justify-center text-gray-700">
      <div class="w-2/3 md:w-2/3 sm:w-5/6">
        <Catalogs :countries="countries"/>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
import Catalogs from '../components/Catalogs.vue'

export default {
  name: 'HomeView',
  data() {
    return {
      countries: [],
    }
  },
  components: {
    Catalogs,
  },
  methods: {

    // Get Countries 
    async fetchCountries() {
      await axios
        .get('https://restcountries.com/v3.1/all')
        .then((response) => {
          this.countries = response.data
        })
        .catch((error) => {
          console.error(error)
        })
    },
  },
  created() {
    this.fetchCountries()
  }
}
</script>
