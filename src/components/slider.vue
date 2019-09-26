<template>
  <div id="touchable">
    <div class="slider-container">
      <div class="slider-container-cards">
        <slot name="cards" />
      </div>
      <div class="slider-container-bullets">
        <slot name="bullets" />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'slider',
}
</script>
<style>
  #touchable {
    background-color: darkgray;
    color: white;
    height: 90vh;
    line-height: 10em;
    font-size: 1.2em;
    text-align: center;
    width: 100%;
  }

  #touchable span {
    margin: 4px;
    border: 1px solid;
    padding: 4px;
    border-radius: 2px;
  }
</style>