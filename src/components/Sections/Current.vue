<template>
  <div class="current-wrapper">
    <div class="current-location">Current Weather</div>
    <div class="current-temperature">{{this.currentWeather.temperature}}</div>
  </div>
</template>

<script>
export default {
  name: 'Current',

  props: ['currentWeather'],

  data () {
    return {

    }
  }
}
</script>

<style>

</style>
