<template>
  <div>
    <Header @btn-search="searchCountries" />
    <div class="flex justify-center text-gray-700">
      <div class="w-2/3 md:w-2/3 sm:w-5/6">
        <!-- Sort -->
        <div class="flex justify-end p-5">
          <label class="text-sm pr-5">Sort by Country Name:</label>
          <select v-model="sortOrder" @change="sortCountries" class="bg-gray-100 text-sm focus:outline-none">
            <option value="asc">Ascending</option>
            <option value="desc">Descending</option>
          </select>
        </div>
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
import Header from '../components/Header.vue'
import Catalogs from '../components/Catalogs.vue'
import Pagination from '../components/Pagination.vue'

export default {
  name: 'HomeView',
  data() {
    return {
      countries: [],
      searchQuery: '',
      sortOrder: 'asc',
      visibleCountries: [],
      currentPage: 0,
      pageSize: 25,
      totalRows:0,
    }
  },
  components: {
    Catalogs,
    Pagination,
    Header,
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

    // Search Countries by name
    async searchCountries(query) {
      if(query !== '') {
        await axios
          .get(`https://restcountries.com/v3.1/name/${query}`)
          .then(response => {
            this.totalRows = response.data.length
            this.visibleCountries = response.data.slice(
            this.currentPage * this.pageSize,(this.pageSize * this.currentPage) + this.pageSize
          )
        })
        .catch(error => {
          console.error(error)
        })
      }
    },
    
    // Sort Countries by country's name
    async sortCountries() {
      const order = this.sortOrder
      await axios
      .get('https://restcountries.com/v3.1/all')
      .then(response => {
        let result  = response.data.sort((country1,country2) => {
          country1 =country1.name.official
          country2 = country2.name.official
          if(order === 'asc') {
            if(country1 < country2) return -1
            // else if(country1 > country2) return 1
        
          }else if (order ==='desc') {
            if(country1 > country2) return -1
            // else if (country1 < country2) return 1
          }
        })

        this.visibleCountries = result.slice(this.currentPage * this.pageSize,(this.pageSize * this.currentPage) + this.pageSize)
      })
      .catch(error => {
        console.error(error)
      })
    }
  },
  created() {
    this.fetchCountries()
  }
}
</script>
