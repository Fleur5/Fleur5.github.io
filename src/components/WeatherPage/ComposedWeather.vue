<template>
  <div class="weather-panel">
    <h3> {{ convertTime(weatherData.dt)}} </h3>
     <div>
      <weather-data class="left-side"
        :name="weatherData.weather[0].main"
        :description="weatherData.weather[0].description"
        :iconId="weatherData.weather[0].icon"/>
      <temperature-data class="right-side"
        :time="weatherData.dt"
        :real="weatherData.temp"
        :feelsLike="weatherData.feels_like"/>
     </div>
     <div>
      <sun-data class="left-side"
        :sunrise="weatherData.sunrise"
        :sunset="weatherData.sunset"
        :uv="weatherData.uvi"
        :clouds="weatherData.clouds"/>
      <wind-data class="right-side"
        :speed="weatherData.wind_speed"
        :gust="weatherData.wind_gust"
        :degree="weatherData.wind_deg"/>
     </div>
  </div>
</template>

<script>
import SunData from './SunData.vue'
import TemperatureData from './TemperatureData.vue'
import WeatherData from './WeatherData.vue'
import WindData from './WindData.vue'
export default {
  name: 'WeatherDetails',
  components: {
    WindData,
    WeatherData,
    SunData,
    TemperatureData
  },
  props:{
    weatherData: null
  },
  methods: {
      convertTime(unixTime) {
          return new Date(unixTime).getDate()
      }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

.weather-panel {
  margin: auto;
  border-radius: 10px;
  height: 200px;
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
