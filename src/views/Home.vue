<template>
  <v-container fluid>
    <v-slide-y-transition mode="out-in">
      <v-layout column align-center>

        <v-text-field
                v-if="windowWidth > 410"
                v-model="num"
                :rules="numberRules"
                label="Введите количество слайдов"
                required
        ></v-text-field>
        <Sliders :img="imageArr" :num="Number(num)"/>
        <div style="height: 3500px">

        </div>
      </v-layout>
    </v-slide-y-transition>
  </v-container>
</template>


<script>
  import Sliders from '../components/Sliders'
  import Urls from '../assets/Urls'

  const unsplashUrl = 'https://api.unsplash.com/photos/?client_id=207516def8772fd9bb8659348cf256a09674965e30fdf49ac376e4efc5cb2d69';

  export default {
    data() {
      return {
        num: 3,
        windowWidth: window.innerWidth,
        imageArr: [],
        numberRules: [
          v => !!v || 'Обязательное поле',
          v => !isNaN(v) || 'Только числа',
          v => v <= 5 || 'Слайдов должно быть не более 5'
        ]
      }
    },
    components: {
      Sliders
    },
    created: function () {
      console.log(Urls)
      this.imageArr = Urls
    },
    mounted() {
      window.onresize = (event) => {
        this.windowWidth = window.innerWidth;
      };
    }
  }
</script>


<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .v-text-field__slot {
    width: 30vw;
  }
</style>
