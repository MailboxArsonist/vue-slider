<template>
  <div id="slider__app">
    <div ref="sliderTrack" class="slider__container">
      <div ref="cardsContainer" class="slider__container__cards" v-on:scroll="handleScroll">
        <slot name="cards" />
        <div 
          v-if="extraSpaceNeeded"
          class="slider__card__placeholder"
          :style="{width: extraSpace + 'px'}" />
      </div>
      <div class="slider__container__bullets">
        <span 
          v-for="(n, index) in amountOfSlides" 
          :key="n"
          :class="{
            'slider__bullet__active' : bulletActive === index
          }"
          @click="bulletClick(index)"
          class="slider__bullet" />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'slider',
  props: {
    settings:{
      default: () => {},
      type: [Object],
      required: true
    },
  },
  data: () => ({
    containerWidth: null,
    amountOfSlides: 0,
    bulletActive: 0,
    slideWidth: 0,
    extraSpaceNeeded: true,
  }),
  created(){
    const { perView } = this.slideSettings
    this.$nextTick(function() {
      this.containerWidth = this.$refs.sliderTrack.clientWidth
      const cards = this.$refs.sliderTrack.querySelectorAll('.slider__card')
      this.amountOfSlides = cards.length
      this.slideWidth = this.containerWidth / perView
      cards.forEach(card => {
        card.style.width = `${this.slideWidth}px`
        })
    });
  },
  computed: {
    slideSettings(){
      return { ...this.settings }
    },
    extraSpace(){
      return this.slideWidth * (this.slideSettings.perView - 1)
    }
  },
  methods: {
    handleScroll(evt){
      this.bulletActive = Math.round(evt.target.scrollLeft / this.slideWidth)
    },
    bulletClick(bulletClicked){
      const goTo = bulletClicked * this.slideWidth
      this.$refs.cardsContainer.scrollLeft = Math.round(bulletClicked * this.slideWidth) 
    }
  }
}
</script>
<style lang="scss">
  #slider__app {
    background-color: #fefefe;
    color: black;
    height: auto;
    overflow: hidden;
  }
  .slider__container__cards {
    display: flex;
    flex-direction: row;
    flex-wrap: nowrap;
    overflow-y: hidden;
    overflow-x: scroll;
    -webkit-overflow-scrolling: touch;
    scroll-behavior: smooth;
    scrollbar-width: none;
    &::-webkit-scrollbar {
      display: none;
    }
  
  }
  .slider__card {
    background: #fff;
    padding: 0.4em 0.5em;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    flex-shrink: 0;
    flex: 0 0 auto;
    box-sizing: border-box;
  }
  .slider__card__placeholder {
    flex: 0 0 auto;
    background: transparent;
  }
  .slider__container__bullets {
    display: flex;
    flex-direction: row;
    justify-content: center;
    align-items: center;
    flex-wrap: nowrap;
    padding: 1em 0;
  }
  .slider__bullet {
    width: 10px;
    height: 10px;
    padding: 0;
    border-radius: 50%;
    border: 2px solid transparent;
    transition: all .3s ease-in-out;
    cursor: pointer;
    line-height: 0;
    box-shadow: 0 .25em .5em 0 rgba(0,0,0,.1);
    margin: 0 .25em;
    display: inline-block;
    background: #fefefe;
  }
  .slider__bullet__active {
    background: #42b883;
  }

</style>