<template>
  <div>
     <h3> {{name}} </h3>
     <p> {{description}} </p>
  </div>
</template>

<script>
export default {
  name: 'WeatherDetails',
  props:{
    name: String,
    description: String,
    iconId: String
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
