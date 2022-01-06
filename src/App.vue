<template>
  <img src="./assets/logo.png" />
  <AircraftsData />
  <AirportData />
</template>

<script>
import AircraftsData from './components/AircraftsData.vue'
import AirportData from './components/AirportData.vue'

export default {
  name: 'App',
  components: {
    AircraftsData,
    AirportData
  }
}
</script>

<style>
img{
  border-radius: 100%;
  border: 3px solid red;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
