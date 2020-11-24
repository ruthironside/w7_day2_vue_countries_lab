<template lang="html">
  <div id="favourite_countries">
    <h2>Favourite Countries</h2>
    <h2> Country Name</h2>
    <p>{{country.name}}</p>
    <p> Population:  </p>
    <p> {{country.population}}</p>
    <img class="lrg-flag" :src="country.flag"/>
  </div>
</template>

<script>
export default {
  name: 'favourite-countries',
  props: ['country']
}
</script>

<style lang="css" scoped>
</style>
