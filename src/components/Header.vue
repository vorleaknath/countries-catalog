<template>
  <div class="flex justify-center bg-white h-24 px-4 shadow">
    <form @submit="onSubmit" class="w-2/3 md:w-2/3 sm:w-5/6 my-6 mx-4 bg-gray-100 rounded  hover:shadow">
      <div class="flex justify-between ">
        <input type="text" v-model="searchQuery" placeholder="Enter Country Name..." class="bg-inherit text-sm text-normal text-gray-600 py-2 px-4 focus:outline-none w-full">
        <input type="submit"  value="Search" class="bg-gray-500 hover:bg-inherit hover:text-gray-700 text-white py-3 px-3 rounded"/>
      </div>
    </form>
  </div>
</template>

<script>
export default {
  name: 'Header',
  data() {
    return {
      searchQuery: ''
    }
  },
  methods: {
    onSubmit(e) {
      e.preventDefault()

      const searchQuery = this.searchQuery

      this.$emit('btn-search', searchQuery)
    }
  }
}
</script>
