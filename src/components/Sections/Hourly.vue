<template>
  <div class="hourly-wrapper">
    <div class="hourly-hours" v-if="hasHourlyWeather" v-for="hour in hourlyForecast">
      <div class="hourly-hour">{{ hour.hour }}</div>
      <div class="hourly-temperature">{{ Math.round(hour.temperature) }}°</div>
      <div class="hourly-precip">{{ Math.round(hour.precipProbability*100)}}%</div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Hourly',

  props: ['hourlyWeather'],

  data () {
    return {
      hasHourlyWeather: false,
      hourlyForecast: []
    }
  },

  mounted() {
    for(let i = 1; i <= 24; i++) {
      let date = new Date(this.hourlyWeather.data[i].time*1000);

      this.hourlyWeather.data[i].hour = date.getHours();
      this.hourlyForecast.push(this.hourlyWeather.data[i]);
    }
    this.hasHourlyWeather = true;
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
    border: 2px solid #dd0cba;
    border-radius: 5px;
    padding-left: 4px;
    padding-right: 4px;
    /* box-shadow: 0 1px 15px 1px rgba(39,39,39,.1); */
  }

  ::-webkit-scrollbar {
    width: 0px;  /* remove scrollbar space */
    background: transparent;  /* optional: just make scrollbar invisible */
  }
</style>
