<template>
  <div
    v-if="!cookieAccepted"
    class="fixed top-0 bottom-0 right-0 left-0 w-full h-full bg-[#00000099]"
  >
    <div
      class="fixed top-1/2 left-1/2 transform -translate-x-1/2 -translate-y-1/2 lg:w-1/3 lg:h-1/3 p-8 gap-8 rounded-lg shadow-lg border bg-gray-100 flex flex-col justify-between items-center"
    >
      <div class="flex flex-col justify-center items-center gap-4">
        <h1
          class="text-gray-600 text-3xl flex flex-row justify-between items-center gap-2"
        >
          <span>Sütik</span>
          <IconCookies class="w-8 h-fit text-amber-600" />
        </h1>
        <p class="text-justify text-sm lg:text-xl text-gray-600 font-normal">
          Ez a weboldal sütiket (cookies) használ, hogy segítse az azonosítást,
          a navigációt és egyéb hasznos funkciókat. Az oldal használatával
          elfogadja, hogy sütiket helyezzünk el az eszközén.
        </p>
      </div>
      <div class="flex flex-row justify-center items-center gap-4">
        <button
          @click="acceptCookies"
          class="px-4 py-2 border rounded-lg bg-amber-600 hover:bg-amber-700 text-white"
        >
          Elfogad
        </button>
        <button
          @click="declineCookies"
          class="px-4 py-2 border rounded-lg text-gray-600 bg-gray-200 hover:bg-gray-300"
        >
          Elutasít
        </button>
      </div>
    </div>
  </div>
</template>

<script setup>
import IconCookies from "@/components/icons/IconCookies.vue";
import { ref } from "vue";

const cookieAccepted = ref(false);

const acceptCookies = () => {
  document.cookie =
    "cookieAccepted=true; expires=Fri, 31 Dec 9999 23:59:59 GMT; path=/";
  cookieAccepted.value = true;
};

const declineCookies = () => {
  document.cookie =
    "cookieAccepted=false; expires=Fri, 31 Dec 9999 23:59:59 GMT; path=/";
  cookieAccepted.value = true;
};

const checkCookie = () => {
  const cookies = document.cookie.split("; ");
  for (const cookie of cookies) {
    const [name, value] = cookie.split("=");
    if (name === "cookieAccepted") {
      cookieAccepted.value = value === "true";
      break;
    }
  }
};

onMounted(() => {
  checkCookie();
});
</script>
