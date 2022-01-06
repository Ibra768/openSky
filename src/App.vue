<template>
  <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.3.1/css/bootstrap.min.css" integrity="sha384-ggOyR0iXCbMQv3Xipma34MD+dH/1fQ784/j6cY/iJTQUOhcWr7x9JvoRxT2MZw1T" crossorigin="anonymous">
  <img src="./assets/logo.png" />
  <div id="wrapper">
    <AircraftsData :aircrafts="properties.aircrafts"/>
    <AirportData :airports="properties.allAirports"/>
  </div>
</template>

<script>
import AircraftsData from './components/AircraftsData.vue'
import AirportData from './components/AirportData.vue'

let properties = {
  allAirports: [

    { iata: "LFQQ", name: "Lille, Lesquin" },

    { iata: "LFML", name: "Marseille, Provence" },

    { iata: "KLAX", name: "Los Angeles, Los Angeles" },

    { iata: "OMDB", name: "Dubaï, Dubaï" },

    { iata: "EGLL", name: "Londres, Heathrow" },

    { iata: "VHHH", name: "Hong Kong, Hong Kong" },

    { iata: "KJFK", name: "New York, John F. Kennedy" },

  ],
  aircrafts : []
}
export default {
  name: 'App',
  components: {
    AircraftsData,
    AirportData
  },
  data() {
    return {
      properties
    }
  },
  methods:{

    init(airport = false){

      let that = this;

      if(!airport){
        airport = "LFPG";
      }

      /*
        let to = Date.now();
        let now = to.toString().substr(0,10);
        let oneHourAgo = now - 3600;
      */
      let now = 1641425645;
      let oneHourAgo = 1641339245;

      fetch('https://opensky-network.org/api/flights/departure?airport='+airport+'&begin=' + oneHourAgo + '&end=' + now)
          .then(function (response) {
            return response.json();
          })
          .then(function (data) {
            console.log(data);
            that.properties.aircrafts.push(data.slice(0, 10));
          }).then(function () {
        fetch('https://opensky-network.org/api/flights/arrival?airport='+airport+'&begin=' + oneHourAgo + '&end=' + now).then(function (response) {
          return response.json();
        }).then(function (data) {
          that.properties.aircrafts.push(data.slice(0, 10));
        })
      });

    }

  },
  mounted() {

    let that = this;

    document.getElementById("selectAirport").addEventListener("change",function(){
      that.init(this.value);
    })

    this.init();


  }
}

</script>


<style>
#wrapper{
  display: flex;
}
#wrapper #aircraftsTable{
  width: 60%;
}
#wrapper #airportTable{
  width: 40%;
}
#airportTable{
  position: relative;
}
#airportTable select{
  position: sticky;
  top: 10px;
}
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
