<template>
  <div>
     <h3>Sun</h3>
     <p> Sunrise: {{convertTime(sunrise)}} </p>
     <p> Sunset: {{convertTime(sunset)}} </p>
     <p> UV index: {{uv}} </p>
     <p> Clouds in %: {{clouds}} </p>
  </div>
</template>

<script>
export default {
  name: 'WeatherDetails',
  props:{
    sunrise: Number,
    sunset: Number,
    uv: Number,
    clouds: Number
  },
  methods: {
      convertTime(unixTime) {
          return new Date(unixTime).getTime()
      }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
