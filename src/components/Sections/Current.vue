<template>
  <div class="current-wrapper">
    <div class="current-summary">{{ this.currentWeather.summary }}</div>
    <div class="current-temperatures">
      <div class="current-temperature">{{ Math.round(this.currentWeather.temperature) }}<span class="current-temperature-celsius">°</span></div>
      <div class="current-temperatures-small">
        <div class="current-temperature-feels-like">Feels Like<br><span class="small-temperature feels-like">{{ Math.round(this.currentWeather.apparentTemperature) }}°</span></div>
        <div class="current-temperature-night">Night<br><span class="small-temperature night">6°</span></div>
      </div>
    </div>
    <div class="current-extras">
      <div class="current-pressure"><img src="../../assets/pressure.svg" height="30" width="30"><br>Pressure<br><span class="extra-item">03.22</span></div>
      <div class="current-wind"><img src="../../assets/wind.svg" height="30" width="30"><br>Wind<br><span class="extra-item">{{ Math.round(this.currentWeather.windSpeed) }} km/h</span></div>
      <div class="current-uv-index"><img src="../../assets/uv.svg" height="30" width="30"><br>UV Index<br><span class="extra-item">5</span></div>
    </div>
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

  .current-wrapper {
    display: flex;
    flex-direction: column;
    align-items: flex-start;
    height: 350px;
    color: #340653;
    margin-left: 30px;
  }

  .current-summary {
    font-size: 35px;
    margin-left: 15px;
  }

  .current-temperatures {
    position: relative;
    top: -10px;
    display: flex;
  }

  .current-temperatures-small {
    display: flex;
    flex-direction: column;
    align-items: flex-start;
    margin-top: 45px;
    margin-left: 60px;
  }

  .current-temperature-night {
    margin-top: 10px;
  }

  .small-temperature {
    font-size: 35px;
    font-weight: bold;
    font-family: 'Signika', cursive;
  }

  .feels-like {
    position: relative;
    left: -10px;
  }

  .night {
    position: relative;
    left: -2px;
  }

  .current-temperature {
    font-size: 180px;
    font-family: 'Signika', cursive;
    font-weight: bold;
    margin-left: 15px;
  }

  .current-temperature-celsius {
    position: relative;
    top: -66px;
    font-size: 80px;
  }

  .current-extras {
    position: relative;
    top: -20px;
    display: flex;
    width: 92%;
    justify-content: space-between;
    margin-left: 27px;
  }

  .extra-item {
    font-weight: bold;
    font-size: 20px;
  }
</style>
