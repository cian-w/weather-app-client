<template>
  <div class="main-wrapper" v-bind:class="{ loading: !gotForecast }">
    <div class="current-location" v-if="!gotForecast">Cork</div>
    <div class="loader" v-if="!gotForecast"><img src="../assets/loader.svg"><br>Getting Weather</div>
    <hourly v-if="gotForecast" :hourlyWeather="this.forecast.hourly"></hourly>
    <daily v-if="gotForecast" :dailyWeather="this.forecast.daily"></daily>
    <current class="current" v-if="gotForecast" :currentWeather="this.forecast.currently"></current>
  </div>
</template>

<script>
import axios from 'axios';
import Current from './Sections/Current.vue'
import Hourly from './Sections/Hourly.vue'
import Daily from './Sections/Daily.vue'

export default {
  name: 'Main',

  components: {
    Current,
    Hourly,
    Daily,
  },

  data () {
    return {
      forecast: {},
      gotForecast: false,
    }
  },

  beforeMount () {
    this.getForecast();
  },

  methods: {
    getForecast() {
      axios.get(`http://cianwoods.com:3000/forecast/51.9280109,-8.5922403`)
        .then(response => {
          this.forecast = response.data;
          this.gotForecast = true;
        })
        .catch(error => {
          console.log(error);
        });
    }
  }


}
</script>

<style scoped>
  .main-wrapper {
    position: absolute;
    top: 0;
    left: 0;
    height: 100%;
    width: 100%;
  }

  .loading {
    display: flex;
    flex-direction: column;
    justify-content: center;
  }

  .current {
    position: absolute;
    bottom: 0;
  }
</style>
