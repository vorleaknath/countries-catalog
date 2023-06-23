<template>
  <div>
    <div class="flex justify-center text-gray-700">
      <div class="w-2/3 md:w-2/3 sm:w-5/6">
        <Catalogs :countries="visibleCountries"/>
        <Pagination 
          :currentPage="currentPage" 
          :totalRows="totalRows"
          :pageSize="pageSize"
          @update-page="updatePage"
        />
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
import Catalogs from '../components/Catalogs.vue'
import Pagination from '../components/Pagination.vue'

export default {
  name: 'HomeView',
  data() {
    return {
      countries: [],
      visibleCountries: [],
      currentPage: 0,
      pageSize: 25,
      totalRows:0,
    }
  },
  components: {
    Catalogs,
    Pagination,
  },
  methods: {

    // Get Countries and display 25 rows per page
    async fetchCountries() {
      await axios
        .get('https://restcountries.com/v3.1/all')
        .then((response) => {
          this.countries = response.data
          this.totalRows = this.countries.length
          this.visibleCountries = this.countries.slice( this.currentPage * this.pageSize, (this.pageSize * this.currentPage) + this.pageSize)

        if(this.visibleCountries.length == 0 && this.currentPage > 0) {
          this.updatePage(this.currentPage - 1 )
        }
        })
        .catch((error) => {
          console.error(error)
        })
    },
    // Update page on pagination
    updatePage(pageNumer) {
      this.currentPage = pageNumer
      this.fetchCountries()
    },
  },
  created() {
    this.fetchCountries()
  }
}
</script>
