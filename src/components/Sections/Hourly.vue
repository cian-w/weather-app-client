<template>
  <div class="hourly-wrapper">
    <div class="hourly-hours" v-if="hasHourlyForecast" v-for="hour in hourlyWeather.data.slice(1)">
      <div class="hourly-hour">{{ hour.hour }}</div>
      <div class="hourly-temperature">{{ Math.round(hour.temperature) }}°</div>
      <div class="hourly-wind">{{ Math.round(hour.windSpeed )}}</div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Hourly',

  props: ['hourlyWeather'],

  data () {
    return {
      hasHourlyForecast: false
    }
  },

  mounted() {
    for(let i = 1; i <= 24; i++) {
      let date = new Date(this.hourlyWeather.data[i].time*1000);

      this.hourlyWeather.data[i].hour = date.getHours();
    }
    this.hasHourlyForecast = true;
  },

  methods: {

  }
}
</script>

<style scoped>
  .hourly-wrapper {
    display: flex;
    max-width: 90%;
    overflow-x: scroll;
    margin: auto;
  }

  .hourly-hours {
    display: flex;
    flex-direction: column;
    justify-content: center;
    margin: 5px;
  }

  ::-webkit-scrollbar {
    width: 0px;  /* remove scrollbar space */
    background: transparent;  /* optional: just make scrollbar invisible */
  }
</style>
