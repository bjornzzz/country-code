<template>
  <div>
    <input type="text" v-model="searchTerm" @input="searchCountries" />
    <ul>
      <li v-for="country in searchResults" :key="country.name.common">
        <a href="#" @click="selectCountry(country)">{{ country.name.common }}</a>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  props: {
    countries: {
      type: Array,
      required: true
    }
  },
  data() {
    return {
      searchTerm: '',
      searchResults: []
    }
  },
  methods: {
    searchCountries() {
      if (this.searchTerm) {
        const regex = new RegExp(this.searchTerm, 'i')
        this.searchResults = this.countries.filter(country => regex.test(country.name.common))
      } else {
        this.searchResults = []
      }
    },
    selectCountry(country) {
      this.$emit('country-selected', country)
    }
  }
}
</script>


  
<style lang="scss">
input{
  width: 250px;
  height: 25px;
}


ul {
  list-style: none;

  a {
    text-decoration: none;
    color: white;
  }
}

</style>
