<template>
  <div id="app">
    <div class="fake">
      <template name="cards">
        <img alt="Vue logo" src="./assets/logo.png" />
        <img alt="Vue logo" src="./assets/logo.png" />
        <img alt="Vue logo" src="./assets/logo.png" />
        <img alt="Vue logo" src="./assets/logo.png" />
        <img alt="Vue logo" src="./assets/logo.png" />
        <img alt="Vue logo" src="./assets/logo.png" />
      </template>
      <template name="bullets">

      </template>
    </div>
  </div>
</template>

<script>
import slider from './components/slider.vue'

export default {
  name: 'app',
  components: {
    slider
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  
}
img {
  width: 100px;
  }
  .fake {
    width: 700px;
  }
</style>
