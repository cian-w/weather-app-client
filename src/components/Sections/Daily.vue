<template>
  <div class="daily-wrapper">
    Daily
    <div class="daily-days" v-if="hasDailyForecast" v-for="day in dailyWeather.data.slice(1)">
      <div class="daily-day">{{ day.day }}</div>
      <div class="daily-temperature">{{ Math.round(day.temperatureMax) }}°</div>
      <div class="daily-wind">{{ Math.round(day.windSpeed )}}</div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Daily',

  props: ['dailyWeather'],

  data () {
    return {
      hasDailyForecast: false
    }
  },

  mounted() {
    for(let i = 1; i < this.dailyWeather.data.length; i++) {
      let date = new Date(this.dailyWeather.data[i].time*1000);
      let weekday = new Array(7);
      weekday[0] = "SUN";
      weekday[1] = "MON";
      weekday[2] = "TUE";
      weekday[3] = "WED";
      weekday[4] = "THU";
      weekday[5] = "FRI";
      weekday[6] = "SAT";

      this.dailyWeather.data[i].day = weekday[date.getDay()];
      this.hasDailyForecast = true;
    }
  }
}
</script>

<style scoped>
  .daily-days {
    display: flex;
    justify-content: space-around;
  }
</style>
