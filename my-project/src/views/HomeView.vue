<template>
  <div id="center">
    <SearchBar :countries="countries" @country-selected="showCountryInformation"/>
    <div id="content">
      <h1>{{ selectedCountry ? selectedCountry.name.common : '' }}</h1>
      <h2>{{ selectedCountry ? selectedCountry.capital[0] : '' }}</h2>
      <div id="flag" v-if="selectedCountry && selectedCountry.flags">
        <img :src="selectedCountry.flags.svg" alt="flag">
      </div>
    </div>
  </div>
</template>

<script>
import SearchBar from '../components/SearchBar.vue';

export default {
  components: {
    SearchBar,
  },
  data() {
    return {
      countries: [],
      selectedCountry: null,
    };
  },
  created() {
    // Fetch countries data from API
    fetch('https://restcountries.com/v3.1/all')
      .then(response => response.json())
      .then(data => this.countries = data)
      .catch(error => console.error(error));
  },
  methods: {
    showCountryInformation(country) {
      this.selectedCountry = country;
    }
  }
};
</script>

<style scoped>
#flag {
  width: 500px;
  height: 400px;
}
h2 {
  color: black;
  margin-left: 25px;
}
h1{
  color: black;
  margin-left: 25px;
}
#center {
  margin-top: 50px;
  display: flex;
  flex-direction: row;
  justify-content: space-around;
}

#content {
  background-color: white;
  width: 500px;
  height: 500px;
  border-radius: 10px;
}

img {
  width: 500px;
  height: 400px;
}
</style>
