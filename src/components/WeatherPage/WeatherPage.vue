<template>
  <article v-if="latestResponse">
    <section :class="latestResponse.alerts? 'left-side' : 'centered'">
      <detailed-weather :currentWeather="latestResponse.current"/>
    </section>
    <section class="right-side" v-if="latestResponse.alerts">
      <weather-warning v-for="warning in latestResponse.alerts" :key="warning.event"
        :warning="warning.event"
        :description="warning.description"
        :startTime="warning.start"
        :endTime="warning.end"
        :source="warning.sender_name"/>
    </section>
  </article>
</template>

<script>
import axios from 'axios'
import WeatherWarning from './WeatherWarning.vue';
import DetailedWeather from './DetailedWeather.vue';

export default {
  name: 'WeatherPage',
  components: {
    WeatherWarning,
    DetailedWeather,
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
      await axios.get(`https://54f320c0-ba97-469d-a3d7-f3a62b7d2797.mock.pstmn.io/data/2.5/onecall?lat=${this.lat}&lon=${this.lon}&exclude=minutely`)
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

.left-side {
  float:left;
  width: 50%;
  height: 70%;
  margin-left: 10%;
}

.centered {
  margin-left: 10%;
  margin-right: 10%;
}

.right-side {
  float:right;
}

</style>
