# vue-slider

A simple item slider component to work on desktop and mobile. You can wrap any components / elements inside .

You can simply copy and paste the Slider component code.

## Init the slider

1. In parent component wrap the slider items in a template with a name of #cards.
2. Each slider item will need a classname of 'slider__card'
3. See example below:

```
<template #cards>
  <div 
    v-for="(product, index) in products" 
    :key="index"
    class="slider__card">
    <ProductItem :productInfo="product"/>
  </div>
</template>
```


If you want to see in action simply clone and run project with steps below:

## Project setup
```
npm install
```

### Compiles and hot-reloads for development
```
npm run serve
```

