<template>
  <div>
     <h3>Temperature</h3>
     <p> Real: {{real}} </p>
     <p> Feels like: {{feelsLike}}</p>
  </div>
</template>

<script>
export default {
  name: 'WeatherDetails',
  props:{
    time: Number,
    real: Number,
    feelsLike: Number
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
