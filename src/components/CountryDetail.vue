<template lang="html">
  <div id="selected_country">
    <h2>{{country.name}}</h2>
    <p> Population: {{country.population}} </p>
    <img :src="country.flag" class="lrg-flag" />

    <neighbouring-countries>
    </neighbouring-countries>

</div>
</template>

<script>
import NeighbourCountry from './NeighbourCountry.vue';
export default {
 
  
  name: 'country-detail',
  props: ['country'],
  components: {
    'neighbouring-countries': NeighbourCountry
  }
}
</script>

<style lang="css" scoped>

.lrg-flag {
  height: 100px
}

</style>
