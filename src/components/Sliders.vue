<template>
  <carousel-3d :display='num' border='0'>
    <slide v-for="(slide, i) in img" :index="i" :key="i">
      <template slot-scope="{ index, isCurrent, leftIndex, rightIndex }">
        <img :data-index="index"
             :class="{ current: isCurrent, onLeft: (leftIndex >= 0), onRight: (rightIndex >= 0) }"
             :src="slide.img">
      </template>
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
