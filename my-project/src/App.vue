<template>
    <div>
    <router-link to="/"><button>Home</button></router-link>
    <router-link to="/register"><button>Register</button></router-link>
    <router-view></router-view>
  </div>

</template>


<script>
import HomeView from './views/HomeView.vue';
import RegisterView from './views/RegisterView.vue';

export default {
  components: {
    RegisterView,
    HomeView
},
  data() {
    return {
      countries: [],
      selectedCountry: null
    }
  },
  mounted() {
    fetch('https://restcountries.com/v3.1/all')
      .then(response => response.json())
      .then(data => {
        this.countries = data
      })
      .catch(error => console.log(error))
  },
  methods: {
    showCountryInformation(country) {
      this.selectedCountry = country
    }
  }
}
</script>


<style>
* {
  margin: 0;
  padding: 0;
  font-family: 'Fira Sans', sans-serif;
}
body {
  background-color: #030e1b;
  color: #FFF;
}

button {
  appearance: none;
  border: none;
  background: none;
  cursor: pointer;
  background-color: #2ae5eb;
  font-size: 1.125rem;
  color: #030e1b;
  padding: 0.5rem 1rem;
  border-radius: 0.5rem;
}
</style>
