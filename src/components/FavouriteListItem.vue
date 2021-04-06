<template lang="html">
  <div id="favourite_countries">
    <h2>Favourite Countries</h2>
    <ul v-for="(country, index) in countries" :key="index" :country="country">
      <li>{{country.name}}</li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'favourite-countries',
  props: ['countries']
}
</script>

<style lang="css" scoped>
</style>
e