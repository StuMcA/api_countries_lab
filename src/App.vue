<template>
  <div id="app">

    <label for="country_select">Select a Country:</label>
    <select id="country_select" v-model="selectedCountry">
      <option disabled value="">Select a country</option>
      <option v-for="country in countries" :key="country.alpha3code" :value="country">{{country.name}}</option>
    </select>

    <country-detail v-if="selectedCountry" :country="selectedCountry"></country-detail>

    <button @click="addFavourite">Add Country to favourites</button>

    <favourite-countries :countries="favouriteCountries"></favourite-countries>
</div>

</template>

<script>
import CountryDetail from './components/CountryDetail.vue';
import FavouriteListItem from './components/FavouriteListItem.vue';

export default {
  name: 'App',
  data() {
    return {
      countries: [],
      selectedCountry: null,
      favouriteCountries: []
    }
  },
  components: {
    'country-detail': CountryDetail,
    'favourite-countries': FavouriteListItem
  },
    mounted(){
      this.fetchCountries();
    },
    methods: {
      fetchCountries: function(){
        fetch("https://restcountries.eu/rest/v2/all")
        .then((response) => response.json())
        .then((data) => this.countries = data)
    
      },
     addFavourite: function(){

       let isPresent = false;
       for (let country of this.favouriteCountries){
         if (this.selectedCountry.name === country.name) {
           isPresent = true;
          }
        }
        if(isPresent){
          return
        } else {
          this.favouriteCountries.push(this.selectedCountry)
        }
    }
  }
}
</script>

<style>
.small-flag {
  height: 20px
}



</style>
