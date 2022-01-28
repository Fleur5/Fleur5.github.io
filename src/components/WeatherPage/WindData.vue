<template>
  <div>
     <h3>Wind</h3>
     <p> Speed: {{speed}} </p>
     <p> Gust speed: {{gust}}</p>
     <p> Direction: {{degree}}</p>
  </div>
</template>

<script>
export default {
  name: 'WeatherDetails',
  props:{
    speed: Number,
    gust: Number,
    degree: Number
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
