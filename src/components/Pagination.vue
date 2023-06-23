<template>
  <nav class="flex justify-center bg-white h-20 m-4 rounded mb-10 ">
    <ul class="inline-flex py-4 text-sm font-normal">
      <li>
        <button v-if="showPreviousPage" @click="updatePage(currentPage -1)" class="bg-gray-100 px-2 py-2 rounded-l-lg border border-gray-300 hover:bg-gray-300">Previous </button>
      </li>
      <li>
        <button class="text-sm font-normal px-4 border border-gray-300 py-2">
          {{ currentPage + 1 }} of {{ totalPages() }} Pages
        </button>
      </li>
      <li>
        <button v-if="showNextPage" @click="updatePage(currentPage + 1)" class="bg-gray-100 px-2 py-2 rounded-r-lg border border-gray-300 hover:bg-gray-300 ">Previous</button>
      </li>
    
  </ul>
  </nav>
</template>

<script>
export default {
  name: 'Pagination',
  props: {
    countries: Array,
    totalRows: Number,
    currentPage: Number,
    pageSize: Number
  }, 
  methods: {
    updatePage(pageNumber){
      this.$emit('update-page', pageNumber)
    },
    totalPages() {
      return Math.ceil(this.totalRows / this.pageSize)
    },
    showPreviousPage() {
      return this.currentPage == 0 ? false : true
    },
    showNextPage() {
      return this.currentPage == (this.totalPages() - 1) ? false : true
    }
  },
}
</script>