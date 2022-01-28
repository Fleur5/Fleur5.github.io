<template>
  <input v-model="city" v-on:keyup.enter="searchCity" placeholder="Please enter the name or zip code of the city"/>
  <h2 v-if="!latestResponse"> Please search for a city </h2>
  <city-list-object 
    v-for="cityObject in latestResponse" :key="cityObject"
    @select-city="$emit('select-city', $event)" 
    :name="cityObject.name" 
    :state="cityObject.state" 
    :country="cityObject.country" 
    :lat="cityObject.lat" 
    :lon="cityObject.lon"/>
</template>

<script>
import axios from 'axios'
import CityListObject from './CityListObject.vue';

export default {
  name: 'WeatherDetails',
  components: {
    CityListObject
  },
  emits: ["select-city"],
  data() {
    return {
      latestResponse: null,
      city: null
    };
  },
  methods: {
    async searchCity() {
      if (this.city != null) {
        if (typeof city === Number) {
          try {
            await axios.get(`${process.env.VUE_APP_WEATHER_URL}/geo/1.0/zip?zip=${this.city},DE&appid=${process.env.VUE_APP_APP_ID}`)
            .then(result => {
              this.$emit('select-city', {lon: result.data[0].lon, lat: result.data[0].lat, name: result.data[0].name})
            })
          } catch (e) {
            console.error(e)
          }
        } else {
          try {
            await axios.get(`${process.env.VUE_APP_WEATHER_URL}/geo/1.0/direct?q=${this.city}&appid=${process.env.VUE_APP_APP_ID}`)
            .then(result => {
              if (result.data.length == 1) {
                this.$emit('select-city', {lon: result.data[0].lon, lat: result.data[0].lat, name: result.data[0].name})
              } else {
                this.latestResponse = result.data
              }
            })
          } catch (e) {
            console.error(e)
          }
        }
      }
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

input {
  height: 30px;
  width: 60%;
  margin-bottom:10px;
}

h2 {
  font-size: 40px;
}

</style>
