<template>
  <div id="app">
    <Container v-bind:weather="weather" />
  </div>
</template>

<script>
import Container from './components/Container.vue'

export default {
  name: 'App',
  components: {
    Container
  },
  data(){
    return {
      weather:{
        temp_real: 5,
        temp_feel: -3.5,
        humidity: 5,
        wind: 20
      }
    }
  }
}
</script>

<style>
body {
  margin: 0;
  padding: 0;
}

#app {
  display: flex;
  align-items: center;
  justify-content: center;
  height: 100vh;
  background: rgb(244, 123, 186);
  background: linear-gradient(-25deg, rgba(244, 123, 186, 0.5) 20%, rgba(90, 95, 245, 0.5) 80%);
}
</style>
