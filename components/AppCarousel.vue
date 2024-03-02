<template>
  <carousel
    :items-to-show="1.5"
    :wrapAround="true"
    :autoplay="3000"
    :transition="500"
    class="cursor-grab"
    id="carousel"
  >
    <slide v-for="slide in images" :key="slide">
      <NuxtImg :src="slide" />
    </slide>

    <template #addons>
      <navigation />
      <pagination id="kolbas" />
    </template>
  </carousel>
</template>

<script lang="ts" setup>
import "vue3-carousel/dist/carousel.css";
import { Carousel, Slide, Pagination, Navigation } from "vue3-carousel";

const images = [
  "slides/slideheader0.jpg",
  "slides/slideheader1.jpg",
  "slides/slideheader2.jpg",
  "slides/slideheader3.jpg",
  "slides/slideheader4.jpg",
  "slides/slideheader5.jpg",
  "slides/slideheader6.jpg",
];
</script>

<style lang="css" scoped>
#carousel > div > ol > li > img {
  box-shadow: rgba(0, 0, 0, 0.25) 0px 14px 28px,
    rgba(0, 0, 0, 0.22) 0px 10px 10px;
  border-radius: 0.75rem;
  border: 1px solid #979797;
  margin: 1rem 1rem 3rem;
  width: 100%;
}
</style>
