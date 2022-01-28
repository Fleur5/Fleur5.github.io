<template>
  <h1 v-if="!cityName">Weather Forecast</h1>
  <h1 v-if="cityName"> {{cityName}} </h1>
  <city-selector v-if="!cityName"
     @select-city="onSelectCity"/>
  <weather-page v-if="cityName"
    :lat="lat"
    :lon="lon"/>
</template>

<script>
import CitySelector from './components/CitySelector/CitySelector.vue'
import WeatherPage from './components/WeatherPage/WeatherPage.vue';

export default {
  name: 'App',
  components: {
    CitySelector,
    WeatherPage
  },
  data() {
    return {
      cityName: null,
      lon: null,
      lat: null
    };
  },
  methods: {
    onSelectCity({ lat, lon, name }) {
      this.lat = lat
      this.lon = lon
      this.cityName = name
    }
  }
}
</script>

<style>
#app {
  font-family: Verdana, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

body {
  background-image: url('./assets/background.jpg');
  background-size: cover;
}

h1 {
  font-weight: 400;
  font-size: 72px;
  color: #2D394D;
  text-shadow: 
		-0.0075em 0.0075em 0 #242F40,
		0.005em 0.005em 0 #6A81A6,
		0.01em 0.01em 0 #627799, 
		0.015em 0.015em #596D8C, 
		0.02em 0.02em 0 #506380, 
		0.025em 0.025em 0 #475873,
		0.03em 0.03em 0 #3E4E66,
		0.035em 0.035em 0 #364459;
}
</style>
