<template>
  <div id="airportTable">
    <select id="selectAirport">
      <option v-for="airport in airports" :key="airport.iata" :value="airport.iata">
        {{airport.name}}
      </option>
    </select>
  </div>
</template>

<script>
export default {
  props: {
    'airports' : Array
  },
  mounted() {
  }
}

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
