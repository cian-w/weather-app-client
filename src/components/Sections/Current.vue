<template>
  <div class="current-wrapper">
    <div class="current-location">Cork</div>
    <div class="current-temperature">{{this.currentWeather.temperature}}°C</div>
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

<style>

</style>
