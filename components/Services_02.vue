<template>
  <div class="grid grid-col-12">
    <div class="col-span-12">
      <div class="flex gap-8 mt-16">
        <ContentDoc path="services/block_02" v-slot="{ doc }">
          <div
            class="flex flex-col justify-start items-start border rounded-2xl p-4 shadow-lg w-full bg-gradient-to-r from-cyan-100 to-amber-100"
          >
            <h1
              class="flex flex-row items-center gap-x-2 text-gray-500 font-bold text-2xl mt-2 ml-8"
            >
              <IconNail class="w-12 h-fit" />
              {{ doc.service_title }}
            </h1>
            <div class="flex flex-row justify-between items-end w-full p-8">
              <ul>
                <li
                  v-for="(item, index) in doc.haircut_items"
                  :key="index"
                  class="my-5"
                >
                  <p
                    class="flex flex-row items-center gap-x-2 text-lg text-gray-500 font-semibold"
                  >
                    <IconCheck class="w-8 h-fit text-green-700" />
                    {{ item }}
                  </p>
                </li>
              </ul>
              <ul>
                <h1 class="text-gray-600 font-bold text-xl">
                  {{ doc.haircut_facts_title }}
                </h1>
                <li
                  v-for="(item, index) in doc.haircut_facts"
                  :key="index"
                  class="my-5"
                >
                  <p
                    class="flex flex-row items-center gap-x-2 text-lg text-gray-500 font-semibold"
                  >
                    <IconCheck class="w-8 h-fit text-green-700" />
                    {{ item }}
                  </p>
                </li>
              </ul>
            </div>
          </div>
        </ContentDoc>
        <div class="h-full w-auto block">
          <NuxtImg
            src="fodraszat_01.jpg"
            class="border rounded-2xl p-4 shadow-lg"
          />
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import IconNail from "./icons/IconNail.vue";
import IconCheck from "./icons/IconCheck.vue";
</script>
