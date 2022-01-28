<template>
  <article v-if="latestResponse">
    <section v-if="latestResponse.alerts">
      <weather-warning v-for="warning in latestResponse.alerts" :key="warning.event"
        :warning="warning.event"
        :description="warning.description"
        :startTime="warning.start"
        :endTime="warning.end"
        :source="warning.sender_name"/>
    </section>
    <section>
      <detailed-weather :currentWeather="latestResponse.current"/>
    </section>
    <section v-if="latestResponse.daily">
      <h2> Following Days: </h2>
      <composed-weather v-for="weather in latestResponse.daily" :key="weather.dt" :weatherData="weather"/>
    </section>
  </article>
</template>

<script>
import axios from 'axios'
import WeatherWarning from './WeatherWarning.vue';
import DetailedWeather from './DetailedWeather.vue';
import ComposedWeather from './ComposedWeather.vue';

export default {
  name: 'WeatherPage',
  components: {
    WeatherWarning,
    DetailedWeather,
    ComposedWeather,
  },
  props:{
    lon: Number,
    lat: Number
  },
  data() {
    return {
      latestResponse: null
    };
  },
  async created() {
    try {
      await axios.get(`${process.env.VUE_APP_WEATHER_URL}/data/2.5/onecall?lat=${this.lat}&lon=${this.lon}&exclude=minutely,hourly&units=metric&appid=${process.env.VUE_APP_APP_ID}`)
          .then( result => this.latestResponse = result.data )
      console.log(this.latestResponse)
    } catch (e) {
      console.error(e)
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

section {
  margin-left: 10%;
  margin-right: 10%;
}

h2 {
  font-size: 30px;
  clear: both;
}

</style>
