<template>
  <div id="app">
    <slider class="fake" v-bind:settings="{
       perView: 2,
      }">
      <template #cards>
        <div class="slider-card" ref="test">
          <img alt="Vue logo" src="./assets/logo.png"  />
          <p>Test inside</p>
        </div>
        <div class="slider-card" ref="test">
          <img alt="Vue logo" src="./assets/logo.png"  />
          <p>Test inside</p>
        </div>
        <div class="slider-card" ref="test">
          <img alt="Vue logo" src="./assets/logo.png" />
          <p>Test inside</p>
        </div>
        <div class="slider-card" ref="test">
          <img alt="Vue logo" src="./assets/logo.png" />
          <p>Test inside</p>
        </div>
        <div class="slider-card" ref="test">
          <img alt="Vue logo" src="./assets/logo.png" />
          <p>Test inside</p>
        </div>
        <div class="slider-card" ref="test">
          <img alt="Vue logo" src="./assets/logo.png" />
          <p>Test inside</p>
        </div>
        <div class="slider-card" ref="test">
          <img alt="Vue logo" src="./assets/logo.png" />
          <p>Test inside</p>
        </div>
        <div class="slider-card" ref="test">
          <img alt="Vue logo" src="./assets/logo.png" />
          <p>Test inside</p>
        </div>
        <div class="slider-card" ref="test">
          <img alt="Vue logo" src="./assets/logo.png" />
          <p>Test inside</p>
        </div>
        <div class="slider-card" ref="test">
          <img alt="Vue logo" src="./assets/logo.png" />
          <p>Test inside</p>
        </div>
        <div class="slider-card" ref="test">
          <img alt="Vue logo" src="./assets/logo.png" />
          <p>Test inside</p>
        </div>
        <div class="slider-card" ref="test">
          <img alt="Vue logo" src="./assets/logo.png" />
          <p>Test inside</p>
        </div>
        <div class="slider-card" ref="test">
          <img alt="Vue logo" src="./assets/logo.png" />
          <p>Test inside</p>
        </div>
        <div class="slider-card" ref="test">
          <img alt="Vue logo" src="./assets/logo.png" />
          <p>Test inside</p>
        </div>
        <div class="slider-card" ref="test">
          <img alt="Vue logo" src="./assets/logo.png" />
          <p>Test inside</p>
        </div>
        <div class="slider-card" ref="test">
          <img alt="Vue logo" src="./assets/logo.png" />
          <p>Test inside</p>
        </div>
        <div class="slider-card" ref="test">
          <img alt="Vue logo" src="./assets/logo.png" />
          <p>Test inside</p>
        </div>
        <div class="slider-card" ref="test">
          <img alt="Vue logo" src="./assets/logo.png" />
          <p>Test inside</p>
        </div>
      </template>
    </slider>
    
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
  width: 100%;
  }
  .fake {
    width: 500px;
  }
</style>
