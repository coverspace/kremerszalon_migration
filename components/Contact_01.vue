<template>
  <div class="grid grid-cols-12">
    <div class="col-span-12 my-16">
      <div class="flex flex-col justify-start items-center">
        <ContentDoc path="/contact/block_01" v-slot="{ doc }">
          <div
            class="flex flex-row justify-center lg:justify-start items-center w-full"
          >
            <h1
              class="flex flex-row items-center gap-x-2 m-8 text-gray-500 font-bold text-xl lg:text-3xl mt-2"
            >
              <IconHaircut class="w-8 h-auto" />
              {{ doc.service_text }}
            </h1>
          </div>
          <div
            class="flex flex-col justify-start items-center lg:grid lg:grid-cols-3 gap-4 w-full"
          >
            <div
              v-for="(item, index) in doc.services_staffs"
              :key="index"
              class="flex flex-col justify-start items-start w-full h-full gap-y-1 p-8 rounded-lg border border-gray-50 shadow-lg bg-gradient-to-r from-pink-100 to-amber-100"
            >
              <h1 class="text-gray-500 font-bold text-2xl font-fancy-1">
                {{ item.name }}
              </h1>
              <small
                class="flex flex-row justify-start items-center gap-x-1 text-gray-600 text-lg"
              >
                <IconHaircut v-if="item.order === 1" class="w-8 h-auto" />
                <IconNail v-if="item.order === 2" class="w-8 h-auto" />
                <IconCosmetic v-if="item.order === 3" class="w-8 h-auto" />
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
        </ContentDoc>
      </div>
    </div>
    <div class="col-span-12">
      <ContentDoc path="/contact/block_01" v-slot="{ doc }">
        <div class="flex flex-row justify-center lg:justify-start items-center">
          <h1
            class="flex flex-row items-center gap-x-2 m-8 text-gray-500 font-bold text-xl lg:text-3xl mt-2"
          >
            <IconMap class="w-8 h-auto" />
            {{ doc.map_text }}
          </h1>
        </div>
      </ContentDoc>
      <div class="h-[50vh] w-auto flex border border-gray-300 rounded-lg">
        <iframe
          src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d2758.784868057387!2d20.141726280148315!3d46.25450442232301!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x474488746ea705a9%3A0x358a2adcc37bc2c9!2sKremer%20Szalon!5e0!3m2!1sen!2shu!4v1709464706031!5m2!1sen!2shu"
          style="border: 0"
          allowfullscreen="false"
          loading="lazy"
          referrerpolicy="no-referrer-when-downgrade"
          class="h-full w-full rounded-lg"
        ></iframe>
      </div>
    </div>
  </div>
</template>

<script setup>
import IconHaircut from "@/components/icons/IconHaircut.vue";
import IconCosmetic from "@/components/icons/IconCosmetic.vue";
import IconPhone from "@/components/icons/IconPhone.vue";
import IconNail from "@/components/icons/IconNail.vue";
import IconLink from "@/components/icons/IconLink.vue";
import IconMap from "@/components/icons/IconMap.vue";

const redirectToDomain = (event) => {
  event.preventDefault();
  const link = event.target;
  const url = new URL(link.href);
  const domain = url.hostname.replace(/^www\./, ""); // Remove 'www.' if present
  window.open(`//${domain}`, "_blank");
};
</script>
