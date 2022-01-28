<template>
  <div class="weather-panel">
    <weather-data class="left-side"
      :name="weatherData.weather[0].main"
      :description="weatherData.weather[0].description"
      :iconId="weatherData.weather[0].icon"/>
    <temperature-data class="right-side"
      :time="weatherData.dt"
      :real="weatherData.temp.day"
      :feelsLike="weatherData.feels_like.day"/>
  </div>
</template>

<script>
import TemperatureData from './TemperatureData.vue'
import WeatherData from './WeatherData.vue'
export default {
  name: 'WeatherDetails',
  components: {
    WeatherData,
    TemperatureData
  },
  props:{
    weatherData: null
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

.weather-panel {
  margin: auto;
  border-radius: 10px;
  clear: both;
  height: 150px;
  border-style: outset;
  border-color: #304a36;
  background-image: linear-gradient(to bottom right, #97b89f, #536e5a);
  margin-bottom: 20px
}

.left-side {
  float:left;
  clear: left;
  margin-left: 5%;
  width: 40%;
  height: 150px;
}

.right-side {
  float:right;
  clear: right;
  margin-right: 5%;
  width: 40%;
  height: 150px;
}

</style>
