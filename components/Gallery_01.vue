<template>
  <div class="grid grid-cols-12">
    <div class="col-span-12 my-8">
      <div class="flex flex-row justify-center items-center">
        <ContentDoc path="gallery/block_01" v-slot="{ doc }">
          <div
            class="flex flex-col justify-between items-between gap-x-4 w-full"
          >
            <h1
              class="flex flex-row items-center gap-x-2 my-8 text-gray-600 text-4xl mt-2 ml-8"
            >
              <IconTeam class="w-8 h-fit" />
              {{ doc.service_text }}
            </h1>
            <div
              class="flex flex-row justify-start items-center gap-x-8 w-full"
            >
              <div
                v-for="(item, index) in doc.services_staffs"
                :key="index"
                class="flex flex-col justify-enter items-start w-full p-8 rounded-lg border border-gray-50 shadow-lg bg-gradient-to-r from-pink-100 to-amber-100"
              >
                <h1 class="text-gray-500 font-bold text-2xl font-fancy-1">
                  {{ item.name }}
                </h1>
                <small
                  v-if="item.role"
                  class="flex flex-row justify-start items-center gap-x-1 text-gray-600 text-lg"
                >
                  <IconHaircut v-if="item.order === 1" class="w-8 h-fit" />
                  <IconCamera v-if="item.order === 2" class="w-8 h-fit" />
                  <IconDress v-if="item.order === 3" class="w-8 h-fit" />

                  {{ item.role }}
                </small>
                <a
                  v-if="item.phone"
                  :href="`tel:${item.phone}`"
                  class="flex flex-row justify-start items-center gap-x-1 text-gray-600 text-xl ml-auto mr-0"
                >
                  <IconPhone class="w-6 h-fit" />
                  {{ item.phone }}
                </a>
                <a
                  v-if="item.link"
                  @click="redirectToDomain($event)"
                  :href="`https://${item.link}`"
                  target="_blank"
                  class="flex flex-row justify-start items-center gap-x-1 text-gray-600 text-xl ml-auto mr-0"
                >
                  <IconLink class="w-6 h-fit" />
                  {{ item.link }}
                </a>
              </div>
            </div>
          </div>
        </ContentDoc>
      </div>
    </div>

    <div class="col-span-12 my-8">
      <div class="flex flex-row justify-center items-center">
        <ContentDoc path="gallery/block_01" v-slot="{ doc }">
          <div
            class="flex flex-col justify-between items-between gap-x-4 w-full"
          >
            <h1
              class="flex flex-row items-center gap-x-2 my-8 text-gray-600 text-4xl mt-2 ml-8"
            >
              <IconModel class="w-8 h-fit" />
              <ContentRenderer :value="doc" />
            </h1>
            <div
              class="flex flex-row justify-start items-center gap-x-8 w-full"
            >
              <div
                v-for="(item, index) in doc.modells"
                :key="index"
                class="flex flex-col justify-center items-center w-full p-8 rounded-lg border border-gray-50 shadow-lg bg-gradient-to-r from-cyan-100 to-amber-100"
              >
                <h1 class="text-gray-500 font-bold text-2xl font-fancy-1">
                  {{ item.name }}
                </h1>
              </div>
            </div>
          </div>
        </ContentDoc>
      </div>
    </div>

    <div class="col-span-12 my-16">
      <!-- Gallery -->
      <Carousel
        :itemsToShow="3.75"
        :wrapAround="true"
        :transition="500"
        class="cursor-grab"
        id="carousel"
      >
        <Slide v-for="slide in images" :key="slide">
          <NuxtImg :src="slide" class="carousel__item" />
        </Slide>

        <template #addons>
          <navigation />
          <pagination />
        </template>
      </Carousel>
    </div>
  </div>
</template>

<script setup>
import "vue3-carousel/dist/carousel.css";
import { Carousel, Slide, Pagination, Navigation } from "vue3-carousel";
import IconHaircut from "@/components/icons/IconHaircut.vue";
import IconCamera from "@/components/icons/IconCamera.vue";
import IconDress from "@/components/icons/IconDress.vue";
import IconPhone from "@/components/icons/IconPhone.vue";
import IconLink from "@/components/icons/IconLink.vue";
import IconTeam from "@/components/icons/IconTeam.vue";
import IconModel from "@/components/icons/IconModel.vue";

const redirectToDomain = (event) => {
  event.preventDefault();
  const link = event.target;
  const url = new URL(link.href);
  const domain = url.hostname.replace(/^www\./, ""); // Remove 'www.' if present
  window.open(`//${domain}`, "_blank");
};

const images = [
  "gallery/modell_01.jpg",
  "gallery/modell_02.jpg",
  "gallery/modell_03.jpg",
  "gallery/modell_04.jpg",
  "gallery/modell_05.jpg",
  "gallery/modell_06.jpg",
  "gallery/modell_07.jpg",
  "gallery/modell_08.jpg",
  "gallery/modell_09.jpg",
  "gallery/modell_10.jpg",
  "gallery/modell_11.jpg",
  "gallery/modell_12.jpg",
  "gallery/modell_13.jpg",
  "gallery/modell_14.jpg",
  "gallery/modell_15.jpg",
  "gallery/modell_16.jpg",
  "gallery/modell_17.jpg",
  "gallery/modell_18.jpg",
  "gallery/modell_19.jpg",
  "gallery/modell_20.jpg",
  "gallery/modell_21.jpg",
  "gallery/modell_22.jpg",
  "gallery/modell_23.jpg",
  "gallery/modell_24.jpg",
  "gallery/modell_25.jpg",
  "gallery/modell_26.jpg",
  "gallery/modell_27.jpg",
  "gallery/modell_28.jpg",
  "gallery/modell_29.jpg",
  "gallery/modell_30.jpg",
  "gallery/modell_31.jpg",
  "gallery/modell_32.jpg",
  "gallery/modell_33.jpg",
];
</script>

<style scoped>
#carousel > div > ol > li > img {
  box-shadow: rgba(0, 0, 0, 0.25) 0px 14px 28px,
    rgba(0, 0, 0, 0.22) 0px 10px 10px;
  border-radius: 0.75rem;
  border: 1px solid #979797;
  margin: 2rem 1rem 3rem;
  /* width: 100%; */
}

.carousel__slide {
  padding: 5px;
}

.carousel__viewport {
  perspective: 2000px;
}

.carousel__track {
  transform-style: preserve-3d;
}

.carousel__slide--sliding {
  transition: 0.5s;
}

.carousel__slide {
  opacity: 0.9;
  transform: rotateY(-20deg) scale(0.9);
}

.carousel__slide--active ~ .carousel__slide {
  transform: rotateY(20deg) scale(0.9);
}

.carousel__slide--prev {
  opacity: 1;
  transform: rotateY(-10deg) scale(0.95);
}

.carousel__slide--next {
  opacity: 1;
  transform: rotateY(10deg) scale(0.95);
}

.carousel__slide--active {
  opacity: 1;
  transform: rotateY(0) scale(1.1);
}
</style>
