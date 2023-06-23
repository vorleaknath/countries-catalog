<template>
  <div>
    <div v-for="(country, index) in countries" :key="index">
      <CountryCard @btn-click="getCountry" :country="country"/>
    </div>
  </div>
</template>

<script>
import CountryCard from '../components/CountryCard.vue'

export default {
  name: "Catalogs",
  props: {
    countries: Array,
  },
  components: { 
    CountryCard, 
  },
  data() {
    return {
      countriesInfo: [],
    }
  },
}
</script>