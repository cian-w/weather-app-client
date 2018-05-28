<template>
  <div class="main-wrapper">
    <current :currentWeather="this.forecast.currently"></current>
    </div>
  </div>
</template>

<script>
import axios from 'axios';
import Current from './Sections/Current.vue'

export default {
  name: 'Main',

  components: {
    Current
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
      axios.get(`http://localhost:3000/forecast/51.9280109,-8.5922403`)
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

<style>

</style>
