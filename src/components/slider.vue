<template>
  <div id="touchable">
    <div ref="sliderTrack" class="slider-container">
      <div ref="cardsContainer" class="slider-container-cards" v-on:scroll="handleScroll">
        <slot name="cards" />
      </div>
      <div class="slider-container-bullets">
        <span 
          v-for="index in amountOfSlides" 
          :key="index"
          :class="{
            'slider-bullet--active' : bulletActive === index
          }"
          @click="bulletClick(index)"
          class="slider-bullet" />
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
    bulletActive: 1,
    slideWidth: 0
  }),
  created(){
    const { perView } = this.slideSettings
    // document.querySelector('.slider-container-cards').addEventListener('scroll', this.handleScroll)
    this.$nextTick(function() {
      this.containerWidth = this.$refs.sliderTrack.clientWidth
      const cards = this.$refs.sliderTrack.querySelectorAll('.slider-card')
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
    }
  },
  methods: {
    handleScroll(evt){
      // window.addEventListener("touchend", window.removeEventListener("touchend"))
      console.log(evt.target.scrollLeft)
      this.bulletActive = Math.floor(evt.target.scrollLeft / this.slideWidth) + 1
    },
    bulletClick(bulletClicked){
      console.log(bulletClicked)
      console.log(this.$refs.cardsContainer.scrollLeft)
    }
  }
}
</script>
<style lang="scss">
  #touchable {
    background-color: #fefefe;
    color: black;
    height: auto;
    overflow: hidden;
  }
  .slider-container-cards {
    display: flex;
    flex-direction: row;
    flex-wrap: nowrap;
    overflow-y: hidden;
    overflow-x: scroll; /* has to be scroll, not auto */
    -webkit-overflow-scrolling: touch;
    scrollbar-width: none;
  
  }
  .slider-card {
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
  .slider-bullet {
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
    background: red;
  }
  .slider-bullet--active {
    background: blue;
  }
</style>