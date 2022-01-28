<template>
  <div class="warning">
     <h3> {{warning}} </h3>
     <p style="white-space: pre;"> {{description}} </p>
     <p class="small"> {{convertTime(startTime)}} - {{convertTime(endTime)}} </p>
     <p class="small"> source: {{source}} </p>
  </div>
</template>

<script>
export default {
  name: 'WeatherDetails',
  props:{
    warning: String,
    description: String,
    startTime: Number,
    endTime: Number,
    source: String
  },
  methods: {
      convertTime(unixTime) {
          return Date(unixTime)
      }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

.warning {
  margin: auto;
  border-radius: 10px;
  border-style: outset;
  border-color: #ed4f3e;
  background-image: linear-gradient(to bottom right, #ed3b3e, #ba1c00);
  margin-bottom: 20px
}

p {
  color:white
}

h3 {
  color: whitesmoke;
}

.small {
  font-size: 10px;
}

</style>
