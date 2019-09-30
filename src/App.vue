<template>
  <div id="app">
    <slider class="fake" :settings="{
       perView: 4,
       breakpoints: {
          1024: { perView: 3 },
          480: { perView: 2.5 },
          300: {perView: 1}
        }
      }">
      <template #cards>
        <div class="slider__card" >
          <img alt="Vue logo" src="./assets/logo.png"  />
          <p>A bunch of placeholder text :) </p>
        </div>
        <div class="slider__card" >
          <img alt="Vue logo" src="./assets/logo.png"  />
          <p>A bunch of placeholder text :) </p>
        </div>
        <div class="slider__card" >
          <img alt="Vue logo" src="./assets/logo.png"  />
          <p>A bunch of placeholder text :) </p>
        </div>
        <div class="slider__card" >
          <img alt="Vue logo" src="./assets/logo.png" />
          <p>A bunch of placeholder text :) </p>
        </div>
        <div class="slider__card" >
          <img alt="Vue logo" src="./assets/logo.png" />
          <p>A bunch of placeholder text :) </p>
        </div>
        <div class="slider__card" >
          <img alt="Vue logo" src="./assets/logo.png" />
          <p>A bunch of placeholder text :) </p>
        </div>
        <div class="slider__card" >
          <img alt="Vue logo" src="./assets/logo.png" />
          <p>A bunch of placeholder text :) </p>
        </div>
        <div class="slider__card" >
          <img alt="Vue logo" src="./assets/logo.png" />
          <p>A bunch of placeholder text :) </p>
        </div>
        <div class="slider__card" >
          <img alt="Vue logo" src="./assets/logo.png" />
          <p>A bunch of placeholder text :) </p>
        </div>
        <div class="slider__card" >
          <img alt="Vue logo" src="./assets/logo.png" />
          <p>A bunch of placeholder text :) </p>
        </div>
        <div class="slider__card" >
          <img alt="Vue logo" src="./assets/logo.png" />
          <p>A bunch of placeholder text :) </p>
        </div>
        <div class="slider__card" >
          <img alt="Vue logo" src="./assets/logo.png" />
          <p>A bunch of placeholder text :) </p>
        </div>
        <div class="slider__card" >
          <img alt="Vue logo" src="./assets/logo.png" />
          <p>A bunch of placeholder text :) </p>
        </div>
        <div class="slider__card" >
          <img alt="Vue logo" src="./assets/logo.png" />
          <p>A bunch of placeholder text :) </p>
        </div>
        <div class="slider__card" >
          <img alt="Vue logo" src="./assets/logo.png" />
          <p>A bunch of placeholder text :) </p>
        </div>
        <div class="slider__card" >
          <img alt="Vue logo" src="./assets/logo.png" />
          <p>A bunch of placeholder text :) </p>
        </div>
        <div class="slider__card" >
          <img alt="Vue logo" src="./assets/logo.png" />
          <p>A bunch of placeholder text :) </p>
        </div>
        <div class="slider__card" >
          <img alt="Vue logo" src="./assets/logo.png" />
          <p>A bunch of placeholder text :) </p>
        </div>
        <div class="slider__card" >
          <img alt="Vue logo" src="./assets/logo.png" />
          <p>A bunch of placeholder text :) </p>
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

<style lang="scss">
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
    width: 700px;
    margin: 2em auto;
    @media (max-width: 800px) {
      width: 80%; 
      background: red;  
    }
  }
</style>
