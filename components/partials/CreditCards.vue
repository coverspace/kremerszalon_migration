<template>
  <div
    class="hidden lg:flex flex-row justify-end items-center gap-x-4 p-2 border-b w-full"
  >
    Products_NetlifySetup
    <small class="text-gray-500 font-normal text-sm"
      >Elfogadott hitelkártyák</small
    >
    <NuxtImg
      v-for="logo in logos"
      :src="logo"
      class="h-6 w-auto border py-1 px-2 rounded bg-gray-50"
    />
  </div>
</template>

<script setup>
const logos = [
  "cards/Mastercard-logo.svg",
  "cards/Visa_Inc._logo.svg",
  "cards/Google_Pay_Logo.svg",
  "cards/Apple_Pay_logo.svg",
];
</script>
