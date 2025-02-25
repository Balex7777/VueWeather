<template>
  <div id="app">
    <Container v-bind:weather="weather" />
  </div>
</template>

<script>
import axios from "axios";
import Container from "./components/Container.vue";

export default {
  name: "App",
  components: {
    Container,
  },
  data() {
    return {
      weather: {
        temp_real: 0,
        temp_feel: 0,
        humidity: 0,
        wind: 0,
      },
    };
  },
  methods: {
    async fetchWeather() {
			const options = {
				method: 'GET',
				url: 'https://weatherapi-com.p.rapidapi.com/current.json',
				params: {q: '55.9, 37.9'},
				headers: {
					'x-rapidapi-key': '544599d2e7msh74eb2e2d65eabc2p19fb54jsnba601a1eee7e',
					'x-rapidapi-host': 'weatherapi-com.p.rapidapi.com'
				}
			};


      try {
				const response = await axios.request(options);
				console.log(response.data);
				const data = response.data;

				this.weather = {
					temp_real: data.current.temp_c,
					temp_feel: data.current.feelslike_c,
					humidity: data.current.humidity,
					wind: data.current.wind_kph,
				};
			} catch (error) {
				window.alert(error);
			}
    },
  },
  mounted() {
    this.fetchWeather();
  },
};
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