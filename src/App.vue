<template>
  <div id="app">
    <carousel>
      <slide v-for="slide in slides" :index="slide.index" :key="slide">
        <img :src="slide.imageUrl" alt="" />
      </slide>
    </carousel>
    <input type="text" v-model="url" placeholder="Entrez une url" />
    <button @click="addSlide">Ajouter une slide</button>
  </div>
</template>

<script>
import Carousel from "./components/Carousel";
import Slide from "./components/Slide";
export default {
  components: {
    Carousel,
    Slide,
  },
  data() {
    return {
      url: "",
      slides: [
        {
          index: 0,
          imageUrl:
            "https://media.routard.com/image/53/1/fotolia-92030325-s.1452531.c1000x300.jpg",
        },
      ],
    };
  },
  methods: {
    addSlide() {
      this.slides.push({ index: this.slides.length, imageUrl: this.url });
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

img {
  width: 100%;
  height: 400px;
}
</style>
