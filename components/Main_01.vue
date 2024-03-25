<template>
  <div class="grid grid-cols-12">
    <div class="col-span-12">
      <div class="flex flex-col justify-center items-center my-2 mx-8 lg:mx-0">
        <ContentDoc path="main/block_01" v-slot="{ doc }" class="flex flex-row">
          <h1 class="text-4xl text-center text-gray-600 my-8">
            {{ doc.description }}
          </h1>
          <div
            class="flex flex-row justify-between border rounded-2xl p-4 my-4 shadow-lg bg-gradient-to-r from-yellow-100 to-pink-100"
          >
            <IconQuote class="hidden lg:block w-32 h-auto rotate-180" />
            <ContentRenderer
              :value="doc"
              class="text-justify text-xl m-4 text-gray-600 font-fancy-1b"
            />
            <IconQuote class="hidden lg:block w-32 h-auto mt-auto mb-0" />
          </div>
        </ContentDoc>
        <div
          class="flex flex-col lg:flex-row justify-center gap-x-8 items-center w-full"
        >
          <NuxtImg
            src="team_02.jpg"
            class="border rounded-2xl p-4 my-8 shadow-lg"
          />
          <NuxtImg
            src="team_01.jpg"
            class="border rounded-2xl p-4 my-8 shadow-lg"
          />
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import IconQuote from "./icons/IconQuote.vue";
</script>
