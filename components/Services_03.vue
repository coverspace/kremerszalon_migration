<template>
  <div class="grid grid-cols-12">
    <div class="col-span-12">
      <div
        class="flex flex-col lg:flex-row justify-between items-center gap-8 mt-16 mx-8 lg:mx-0"
      >
        <ContentDoc path="services/block_03" v-slot="{ doc }">
          <div
            class="flex flex-col justify-start items-start border rounded-2xl p-4 shadow-lg w-full bg-gradient-to-r from-cyan-100 to-amber-100"
          >
            <h1
              class="flex flex-row items-center gap-x-2 text-gray-500 font-bold text-2xl mt-4 ml-8"
            >
              <IconCosmetic class="w-8 h-fit" />
              {{ doc.service_title }}
            </h1>
            <div
              class="flex flex-col lg:flex-row justify-between items-start w-full p-8"
            >
              <ul class="w-full">
                <li
                  v-for="(item, index) in doc.cosmetic_items"
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
              <div
                class="flex flex-col justify-start items-start gap-y-8 w-full"
              >
                <div
                  v-for="(item, index) in doc.services_staffs"
                  :key="index"
                  class="flex flex-col justify-start items-start w-full gap-y-1 p-8 rounded-lg border border-gray-50 shadow-lg bg-glass"
                >
                  <h1 class="text-gray-500 font-bold text-2xl font-fancy-1">
                    {{ item.name }}
                  </h1>
                  <small
                    class="flex flex-row justify-start items-center gap-x-1 text-gray-600 text-lg"
                  >
                    <IconCosmetic class="w-8 h-fit" />
                    {{ item.role }}
                  </small>
                  <a
                    :href="`tel:${item.phone}`"
                    class="flex flex-row justify-start items-center gap-x-1 text-gray-600 text-xl ml-auto mr-0"
                  >
                    <IconPhone class="w-6 h-fit" />
                    {{ item.phone }}
                  </a>
                  <a
                    v-if="item.link"
                    :href="`https://www.${item.phone}`"
                    target="_blank"
                    class="flex flex-row justify-start items-center gap-x-1 text-gray-600 text-xl ml-auto mr-0"
                  >
                    <IconLink class="w-6 h-fit" />
                    {{ item.link }}
                  </a>
                </div>
              </div>
            </div>
          </div>
        </ContentDoc>
        <div class="h-full w-auto block">
          <NuxtImg
            src="kozmetika_01.jpg"
            class="border rounded-2xl p-4 shadow-lg mb-8"
          />
          <NuxtImg
            src="kozmetika_02.jpg"
            class="border rounded-2xl p-4 shadow-lg"
          />
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import IconCosmetic from "@/components/icons/IconCosmetic.vue";
import IconCheck from "@/components/icons/IconCheck.vue";
import IconPhone from "@/components/icons/IconPhone.vue";
</script>
