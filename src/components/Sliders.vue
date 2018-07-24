<template>
  <carousel-3d :display='num' border='0' :controls-visible="true">
    <slide v-for="(slide, i) in img" :index="i" :key="slide.id">
        <a :href="slide.img" target="_blank">
          <img :data-index="slide.id"
             :src="slide.img">
        </a>
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
</style>
