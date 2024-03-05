<template>
  <div
    v-show="setBar"
    class="h-full overflow-hidden rounded-l-xl border border-gray-100 bg-gradient-to-r from-yellow-200 to-zinc-100"
  >
    <div class="flex flex-col justify-between items-start w-full h-full">
      <div
        class="flex flex-row justify-between items-center border-b-2 border-amber-300 w-full"
      >
        <div
          class="flex flex-row justify-start items-center ml-6 gap-x-2 w-full"
        >
          <IconSidebar class="w-8 h-fit text-gray-600" />
          <h1 class="text-lg text-gray-600 font-semibold">Oldalsáv</h1>
        </div>
        <span @click="$emit('cancel')" class="ml-auto mr-0">
          <IconClose
            class="w-10 h-fit p-2 m-8 text-gray-500 border-2 rounded-lg bg-slate-50 active:bg-slate-200"
          />
        </span>
      </div>
      <!-- Cimlap, Szolgaltatasok, Termekek, Arlista, Galeria, Kapcsolat -->
      <ul class="m-4">
        <li
          v-for="(item, index) in navigationTree"
          :key="index"
          class="flex flex-row justify-start items-center w-full p-4"
        >
          <NuxtLink
            :to="item._path === '/main' ? '/' : item._path"
            class="text-gray-600 font-bold text-xl pb-2"
          >
            {{ item.children[0].title }}
          </NuxtLink>
        </li>
      </ul>
      <div
        class="flex flex-col justify-end items-center w-full h-full border-t-2 border-amber-300 p-4"
      >
        <small class="text-gray-500 font-normal text-sm"
          >Elfogadott hitelkártyák</small
        >
        <div
          class="flex flex-row justify-center items-center gap-x-2 p-2 w-full"
        >
          <NuxtImg
            v-for="logo in logos"
            :src="logo"
            class="h-6 w-auto border py-1 px-2 rounded bg-gray-50"
          />
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import IconClose from "@/components/icons/IconClose.vue";
import IconSidebar from "@/components/icons/IconSidebar.vue";

const props = defineProps({
  setBar: {
    type: Boolean,
  },
  navigationTree: {
    type: Array,
    default: () => [],
  },
});

const emit = defineEmits(["cancel"]);

onMounted(() => {
  console.log("mounted");
});

const logos = [
  "cards/Mastercard-logo.svg",
  "cards/Visa_Inc._logo.svg",
  "cards/Google_Pay_Logo.svg",
  "cards/Apple_Pay_logo.svg",
];
</script>

<style lang="css" scoped>
.router-link-exact-active::before {
  content: "•";
  margin-left: -16px;
  position: absolute;
  color: gray;
}

.router-link-exact-inactive::before {
  content: "•";
  margin-left: -16px;
  position: absolute;
  color: transparent;
}
</style>
