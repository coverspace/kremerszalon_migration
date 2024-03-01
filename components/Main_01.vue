<template>
  <div class="grid grid-col-12">
    <div class="col-span-12">
      <div class="flex flex-col justify-center items-center my-2">
        <div>
          <ContentDoc
            path="main/block_01"
            v-slot="{ doc }"
            class="flex flex-row"
          >
            <h1 class="text-2xl">{{ doc.description }}</h1>
            <div
              class="flex flex-row justify-between border rounded-2xl p-4 my-4"
            >
              <IconQuote class="w-32 h-fit rotate-180" />
              <ContentRenderer
                :value="doc"
                class="text-justify text-xl m-4 text-gray-600 fancy-text-Regular"
              />
              <IconQuote class="w-32 h-fit mt-auto mb-0" />
            </div>
          </ContentDoc>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import IconQuote from "./icons/IconQuote.vue";
</script>
