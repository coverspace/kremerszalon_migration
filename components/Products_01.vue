<template>
  <div class="grid grid-cols-12">
    <div class="col-span-12">
      <div
        class="flex flex-col lg:flex-row justify-between items-center gap-8 mt-16 mx-8 lg:mx-0"
      >
        <div class="flex flex-col justify-start items-end w-full">
          <NuxtImg
            src="logo/every_green_logo.png"
            class="w-full lg:w-1/2 border rounded-2xl p-14 shadow-lg mb-8 bg-gradient-to-r from-cyan-100 to-amber-100"
          />
          <NuxtImg
            src="products/every_green_products.png"
            class="w-full lg:w-4/5 border rounded-2xl p-14 shadow-lg bg-gradient-to-r from-red-100 to-amber-100"
          />
        </div>
        <ContentDoc path="products/block_01" v-slot="{ doc }">
          <div
            class="flex flex-col justify-start items-start border rounded-2xl p-4 shadow-lg w-full bg-gradient-to-r from-red-100 to-amber-100"
          >
            <h1
              class="flex flex-row items-center gap-x-2 text-gray-500 font-bold text-2xl mt-4 ml-8"
            >
              <IconCosmetic class="w-8 h-auto" />
              {{ doc.product_title }}
            </h1>
            <div
              class="flex flex-col lg:flex-row justify-between items-start w-full p-8"
            >
              <ul class="w-full">
                <li
                  v-for="(item, index) in doc.product_items"
                  :key="index"
                  class="my-5"
                >
                  <p
                    class="flex flex-row items-center gap-x-2 text-lg text-gray-500 font-semibold"
                  >
                    <IconCheck class="w-8 h-auto text-green-700" />
                    {{ item }}
                  </p>
                </li>
              </ul>
            </div>
          </div>
        </ContentDoc>
      </div>
    </div>
  </div>
</template>

<script setup>
import IconCosmetic from "@/components/icons/IconCosmetic.vue";
import IconCheck from "@/components/icons/IconCheck.vue";
import IconPhone from "@/components/icons/IconPhone.vue";
</script>
