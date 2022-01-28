<template>
  <div class="city-item">
    <h3> {{ name }} </h3>
    <p v-if="state"> State: {{state}} </p>
    <p> Country: {{country}} </p>
    <button @click="$emit('select-city', {lon: this.lon, lat: this.lat, name: this.name})"> Select City </button>
  </div>
</template>

<script>
export default {
  name: 'CityListObject',
  emits: ["select-city"],
  props:{
    name: String,
    state: null,
    country: String,
    lon: Number,
    lat: Number
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

.city-item {
  margin: auto;
  border-radius: 10px;
  width: 20%;
  border-style: outset;
  border-color: #47311b;
  background-image: linear-gradient(to bottom right, #e3d4ac, #736044);
  margin-bottom: 20px
}

p {
  color:black;
}

button {
  background-color: transparent;
  font-size: 20px;
  width: 100%;
  padding-top: 5px;
  border: none;
}

button:hover {
  border: 1px solid;
  box-shadow: inset 0 0 20px rgba(255, 255, 255, .5), 0 0 20px rgba(255, 255, 255, .2);
  outline-color: rgba(255, 255, 255, 0);
  outline-offset: 15px;
  text-shadow: 1px 1px 2px #427388; 
}

</style>
