<template>
  <carousel-3d :display='num' border='0' :controls-visible="true" dir = "ltr">
    <slide v-for="(slide, i) in img" :index="i" :key="slide.id">
        <figure>
          <img :src="slide.img">
          <figcaption>
            <a :href="slide.img" target="_blank">
              Перейти к источнику
            </a>
          </figcaption>
        </figure>
    </slide>
  </carousel-3d>
</template>

<script>
  import {Carousel3d, Slide} from 'vue-carousel-3d';

  export default {
    name: 'Sliders',
    props: {
      img: Array,
      num: Number
    },
    components: {
      Carousel3d,
      Slide
    }
  }
</script>

<style scoped lang="less">
  .carousel-3d-slide {
    background: #eee;
    display: flex;
    justify-content: center;
    align-items: center
  }
  figcaption a {
    height: 69px;
    display: flex;
    justify-content: center;
    text-decoration: none;
  } 
</style>
