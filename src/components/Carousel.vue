<template>
  <div class="carousel">
    <slot></slot>
    <button class="carousel__prev" @click.prevent="previous">Précédent</button>
    <button class="carousel__next" @click.prevent="next">Suivant</button>
    <div class="carousel__pagination">
      <button
        v-for="n in slidesCount"
        @click.prevent="goto(n - 1)"
        :key="n"
        :class="{ active: n - 1 === index }"
      ></button>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      index: 0,
      slides: [],
      direction: "right",
    };
  },
  methods: {
    next() {
      this.index++;
      this.direction = "right";
      if (this.index >= this.slidesCount) {
        this.index = 0;
      }
    },
    previous() {
      this.index--;
      this.direction = "left";
      if (this.index < 0) {
        this.index = this.slidesCount - 1;
      }
    },
    goto(index) {
      this.direction = index > this.index ? "right" : "left";

      this.index = index;
    },
  },
  computed: {
    slidesCount() {
      return this.slides.length;
    },
  },
  mounted() {
    this.slides = this.$children;
  },
};
</script>

<style>
.carousel {
  position: relative;
  overflow: hidden;
}
.carousel__pagination {
  position: absolute;
  bottom: 50px;
  right: 0;
  left: 0;
}

.carousel__pagination button {
  width: 15px;
  height: 15px;
  margin: 5px;
  padding: 0;
  border: black;
  border-radius: 100%;
  background-color: grey;
}

.carousel__pagination button.active {
  background-color: grey;
  opacity: 50%;
}
</style>
