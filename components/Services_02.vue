<template>
  <div class="grid grid-cols-12">
    <div class="col-span-12">
      <div
        class="flex flex-col-reverse lg:flex-row justify-between items-center gap-8 mt-16 mx-8 lg:mx-0"
      >
        <div class="h-full w-auto block">
          <NuxtImg
            src="mukorom_01.jpg"
            class="border rounded-2xl p-4 shadow-lg mb-8"
          />
          <NuxtImg
            src="mukorom_02.jpg"
            class="border rounded-2xl p-4 shadow-lg"
          />
        </div>
        <ContentDoc path="services/block_02" v-slot="{ doc }">
          <div
            class="flex flex-col justify-start items-start border rounded-2xl p-4 shadow-lg w-full bg-gradient-to-r from-amber-100 to-cyan-100"
          >
            <h1
              class="flex flex-row items-center gap-x-2 text-gray-500 font-bold text-2xl mt-4 ml-8"
            >
              <IconNail class="w-12 h-auto" />
              {{ doc.service_title }}
            </h1>
            <div
              class="flex flex-col lg:flex-row justify-start items-start gap-x-16 p-8"
            >
              <div
                class="flex flex-col justify-between items-between gap-y-4 w-full"
              >
                <h1 class="text-gray-600 font-bold text-xl">
                  {{ doc.nails_text }}
                </h1>
                <ContentRenderer
                  :value="doc"
                  class="text-gray-600 font-normal text-justify text-xl"
                />
                <ul>
                  <li
                    v-for="(item, index) in doc.nails_items"
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
                    <IconNail class="w-8 h-auto" />
                    {{ item.role }}
                  </small>
                  <a
                    :href="`tel:${item.phone}`"
                    class="flex flex-row justify-start items-center gap-x-1 text-gray-600 text-xl ml-auto mr-0"
                  >
                    <IconPhone class="w-6 h-auto" />
                    {{ item.phone }}
                  </a>
                  <a
                    v-if="item.link"
                    @click="redirectToDomain($event)"
                    :href="`https://${item.link}`"
                    target="_blank"
                    class="flex flex-row justify-start items-center gap-x-1 text-gray-600 text-xl ml-auto mr-0"
                  >
                    <IconLink class="w-6 h-auto" />
                    {{ item.link }}
                  </a>
                </div>
              </div>
            </div>
          </div>
        </ContentDoc>
      </div>
    </div>
  </div>
</template>

<script setup>
import IconNail from "@/components/icons/IconNail.vue";
import IconCheck from "@/components/icons/IconCheck.vue";
import IconLink from "@/components/icons/IconLink.vue";
import IconPhone from "@/components/icons/IconPhone.vue";

const redirectToDomain = (event) => {
  event.preventDefault();
  const link = event.target;
  const url = new URL(link.href);
  const domain = url.hostname.replace(/^www\./, ""); // Remove 'www.' if present
  window.open(`//${domain}`, "_blank");
};
</script>
