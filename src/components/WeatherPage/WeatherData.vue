<template>
  <div>
     <img :src="'http://openweathermap.org/img/wn/' + iconId + '@2x.png'"/>
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

img {
  max-height:70px;
  width: auto;
  height: auto;
}

h3 {
  margin-top: 0%;
}

</style>
