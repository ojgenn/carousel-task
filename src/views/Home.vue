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
  .v-text-field {
    width: 30vw;
  }
</style>
