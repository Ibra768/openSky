<template>
  <div id="aircraftsTable">
    <h1>Departs</h1>
    <table class="table">
      <thead>
      <tr>
        <th scope="col">Code ICAO24</th>
        <th scope="col">Destination</th>
      </tr>
      </thead>
      <tbody>
      <tr v-for="departure in aircrafts[0]" :key="departure.icao24">
        <th scope="row">{{departure.icao24}}</th>
        <td>{{departure.estArrivalAirport}}</td>
      </tr>
      </tbody>
    </table>

    <h1>Arrivées</h1>
    <table class="table">
      <thead>
      <tr>
        <th scope="col">Code ICAO24</th>
        <th scope="col">Provenance</th>
      </tr>
      </thead>
      <tbody>
      <tr v-for="arrival in aircrafts[1]" :key="arrival.icao24">
        <th scope="row">{{arrival.icao24}}</th>
        <td>{{arrival.estDepartureAirport}}</td>
      </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  props: {
      'aircrafts' : Array
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
