<template>
  <div id="app">

    <label for="country_select">Select a Country:</label>
    <select id="country_select" v-model="selectedCountry">
      <option disabled value="">Select a country</option>
      <option v-for="country in countries" :key="country.alpha3code" :value="country" >{{country.name}}</option>
    </select>

    <country-detail :country="selectedCountry"></country-detail>

    <button v-on:click="saveFavouriteCountry">Add Country to favourites</button>

    <favourite-countries v-for="country  in favouriteCountries" :key="country.alpha3code" :country="country"></favourite-countries>
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
      selectedCountry: "",
      favouriteCountries: []
    }
  },
  components: {
    'country-detail': CountryDetail,
    'favourite-countries': FavouriteListItem
  },
    mounted(){
      this.listOfCountries()

  },
    methods: {
    listOfCountries: function(){
      fetch("https://restcountries.eu/rest/v2/all")
      .then(response => response.json())
      .then(data => this.countries = data)
    },
    saveFavouriteCountry: function() {
      let isInList = false
      for (country in this.favouriteCountries) {
        if (country.name === this.selectedCountry.name) {
          isInList = true
        }  
      }
      if (!isInList) {
        this.favouriteCountries.push(this.selectedCountry);
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

// "name": "Afghanistan",
// "topLevelDomain": [
// ".af"
// ],
// "alpha2Code": "AF",
// "alpha3Code": "AFG",
// "callingCodes": [
// "93"
// ],
// "capital": "Kabul",
// "altSpellings": [
// "AF",
// "Afġānistān"
// ],
// "region": "Asia",
// "subregion": "Southern Asia",
// "population": 27657145,
// "latlng": [
// 33,
// 65
// ],
// "demonym": "Afghan",
// "area": 652230,
// "gini": 27.8,
// "timezones": [
// "UTC+04:30"
// ],
// "borders": [
// "IRN",
// "PAK",
// "TKM",
// "UZB",
// "TJK",
// "CHN"
// ],