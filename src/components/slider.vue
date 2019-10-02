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
          @mouseenter="hover"
          @mouseleave="hover"
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
    windowWidth: null,
    perView: null,
    from: 0,
  }),
  created(){
    window.addEventListener("resize", () => this.windowWidth = window.innerWidth)
    // this.$nextTick(this.resizeSlides);
    this.windowWidth = window.innerWidth
  },
  mounted(){ 
    this.resizeSlides() 
    this.$refs.cardsContainer.addEventListener('dragstart', this.startMove)
    this.$refs.cardsContainer.addEventListener('dragend', this.endMove)
  },
  destroyed(){
    this.$refs.cardsContainer.removeEventListener('dragstart', this.startMove)
    this.$refs.cardsContainer.removeEventListener('dragend', this.endMove)
    window.removeEventListener("resize", () => this.windowWidth = window.innerWidth)
  },
  computed: {
    slideSettings(){
      return { ...this.settings }
    },
    extraSpace(){
      return this.slideWidth * (this.perView - 1)
    }
  },
  watch: {
    windowWidth(){this.resizeSlides()}
  },
  methods: {
    startMove(e){
      this.$refs.cardsContainer.classList.add('slider__card__grabbing')
      this.from = e.screenX
    },
    hover(e){
      let isMobile = window.matchMedia('(max-width: 500px)')
      if(!isMobile.matches) e.target.classList.toggle('slider__bullet__hover')
    },
    endMove(e){
      if(e.screenX > this.from){
        // Move backwards
        this.$refs.cardsContainer.scrollLeft = Math.round(this.$refs.cardsContainer.scrollLeft + (this.from - e.screenX)) < 0 ? 0 : Math.round((this.$refs.cardsContainer.scrollLeft + (this.from - e.screenX)) / this.slideWidth) * this.slideWidth
      } else {
        // Move forwards
        this.$refs.cardsContainer.scrollLeft = Math.round((this.$refs.cardsContainer.scrollLeft - (e.screenX - this.from)) / this.slideWidth) * this.slideWidth
      }
      this.from = 0
    },
    handleScroll(evt){
      this.bulletActive = Math.round(evt.target.scrollLeft / this.slideWidth)
    },
    bulletClick(bulletClicked){
      this.$refs.cardsContainer.scrollLeft = Math.round(bulletClicked * this.slideWidth) 
    },
    resizeSlides(){
      this.containerWidth = this.$refs.sliderTrack.clientWidth
      const { perView, breakpoints } = this.slideSettings
      this.perView = perView
      if(breakpoints){
        const mqs = Object.entries(breakpoints)
        for( const [ mq, value ] of mqs) {
          if(this.windowWidth <= mq) {
            this.perView = value.perView
            break
          }
        }
      }
      const cards = this.$refs.sliderTrack.querySelectorAll('.slider__card')
      this.amountOfSlides = cards.length
      this.slideWidth = this.containerWidth / this.perView
      cards.forEach(card => {
        card.style.width = `${this.slideWidth}px`
        })
    }
  }
}
</script>
<style lang="scss">
  #slider__app {
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
    padding: 0.4em 0.5em;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    flex-shrink: 0;
    flex: 0 0 auto;
    cursor: grab;
    box-sizing: border-box;
  }
  .slider__card__grabbing {
    cursor: grabbing;
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
    background: black;
    box-sizing: border-box;
    flex-shrink: 0;
  }
  .slider__bullet__hover {
    border-color: #42b883;
  }
  .slider__bullet__active {
    background: #42b883;
  }

</style>