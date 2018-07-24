<template>
  <v-container fluid>
    <v-slide-y-transition mode="out-in">
      <v-layout column align-center>

        <v-text-field
          v-model="num"
          :rules="nameRules"
          label="Введите количество слайдов"
          required
          @input="inputHandler"
        ></v-text-field>
        <carousel-3d :display = 'num'>
          <slide :index="0">
            Slide 1 Content
          </slide>
          <slide :index="1">
            Slide 2 Content
          </slide>
          <slide :index="2">
            Slide 3 Content
          </slide>
          <slide :index="3">
            Slide 4 Content
          </slide>
          <slide :index="4">
            Slide 5 Content
          </slide>
          <slide :index="5">
            Slide 6 Content
          </slide>
          <slide :index="6">
            Slide 7 Content
          </slide>
        </carousel-3d>
        <div style="height: 3500px">
     
        </div>
      </v-layout>
    </v-slide-y-transition>
  </v-container>
</template>


<script>
import { Carousel3d, Slide } from 'vue-carousel-3d';
export default {
  data() {
    return{
      num: 3,
      nameRules: [
        v => !!v || 'Обязательное поле',
        v => !isNaN(v) || 'Только числа',
        v => v <= 5 || 'Слайдов должно быть менее 5'
      ]
    }
  },
  components: {
    Carousel3d,
    Slide
  }
}
</script>


<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
