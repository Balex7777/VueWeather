<template>
	<div>
		<h1 class="title">Погода в Королёве сейчас</h1>
		<div class="informer-container">
        <Temperature v-bind:real="weather.temp_real" v-bind:feel="weather.temp_feel" />
        <div class="flex-break"></div>
        <Humidity v-bind:val="weather.humidity" />
        <div class="vertical-divider"></div>
        <Wind v-bind:val="weather.wind" />
    </div>
	</div>
</template>

<script>
import Humidity from './Humidity.vue'
import Temperature from './Temperature.vue'
import Wind from './Wind.vue'

export default {
    name: "Container",
    props: ['weather'],
    components: { 
        Temperature,
        Wind,
        Humidity
    },
    
}
</script>

<style>
.informer-container {
  display: flex;
  align-items: flex-start;
  justify-content: space-between;
  flex-wrap: wrap;
  width: 400px;
  padding: 30px;
  background-image: url('img/forest.png');
  background-size: cover;
  background-position: center center;
  border-radius: 20px;
  box-shadow: 0px 0px 10px 0px rgba(50, 50, 50, 0.75);
}
.flex-break{
  flex-basis: 100%;
  height: 0;
}

.vertical-divider{
  height: 70px;
  width: 1px;
  background-color: #fff;
  vertical-align: middle;
  display: table-cell;
}
.title{
	font-family: sans-serif;
	font-size: 28px;
	text-align: center;
}
</style>