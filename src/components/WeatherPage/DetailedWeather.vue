<template>
  <div class="weather-panel">
    <h3> TODAY </h3>
     <p> Pressure: {{currentWeather.pressure}}</p>
     <p> Humidity: {{currentWeather.humidity}}</p>
     <p v-if="currentWeather.rain"> Rain Volume in mm: {{currentWeather.rain}}</p>
     <p v-if="currentWeather.snow"> Snow in mm: {{currentWeather.snow}}</p>
     <div>
      <weather-data class="left-side"
        :name="currentWeather.weather[0].main"
        :description="currentWeather.weather[0].description"
        :iconId="currentWeather.weather[0].icon"/>
      <temperature-data class="right-side"
        :time="currentWeather.dt"
        :real="currentWeather.temp"
        :feelsLike="currentWeather.feels_like"/>
     </div>
     <div>
      <sun-data class="left-side"
        :sunrise="currentWeather.sunrise"
        :sunset="currentWeather.sunset"
        :uv="currentWeather.uvi"
        :clouds="currentWeather.clouds"/>
      <wind-data class="right-side"
        :speed="currentWeather.wind_speed"
        :gust="currentWeather.wind_gust"
        :degree="currentWeather.wind_deg"/>
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
    currentWeather: null
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

.weather-panel {
  margin: auto;
  border-radius: 10px;
  height: 550px;
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
