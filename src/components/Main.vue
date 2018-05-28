<template>
  <div v-if="gotForecast">{{this.location.name}}{{this.forecast.currently.temperature}}</div>
</template>

<script>
import axios from 'axios';

export default {
  name: 'Main',

  data () {
    return {
      location: {},
      forecast: {},
      gotForecast: false,
    }
  },

  beforeMount () {
    const options = {
      enableHighAccuracy: true,
      timeout: 10000,
      maximumAge: 0
    };

    navigator.geolocation.getCurrentPosition(this.getLocation, this.locationError, options);
  },

  methods: {
    getLocation(position) {
      this.location.latitude = position.coords.latitude;
      this.location.longitude = position.coords.longitude;

      axios.get(`http://maps.googleapis.com/maps/api/geocode/json?latlng=${this.location.latitude},${this.location.longitude}&sensor=true`)
        .then(response => {
          this.location.name = response.data.results[0].address_components[3].short_name;
          this.getForecast();
        })
        .catch(error => {
          console.log(error);
        });
    },

    locationError(err) {
      console.log('Error getting location!', err);
    },

    getForecast() {
      let coords = `${this.location.latitude},${this.location.longitude}`;

      axios.get(`http://localhost:3000/forecast/${coords}`)
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
