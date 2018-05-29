<template>
  <div class="current-wrapper">
    <div class="current-location">Cork</div>
    <div class="current-temperature">{{ Math.round(this.currentWeather.temperature) }}°</div>
    <div class="current-summary">{{ this.currentWeather.summary }}</div>
    <div class="current-wind">{{ Math.round(this.currentWeather.windSpeed) }}km/h</div>

  </div>
</template>

<script>
export default {
  name: 'Current',

  props: ['currentWeather'],

  data () {
    return {

    }
  },
}
</script>

<style scoped>
  @import url('https://fonts.googleapis.com/css?family=Signika');
  .current-temperature {
    font-size: 140px;
    font-family: 'Signika', cursive;
  }

</style>
