<template>
  <!-- fixed bottom-0 left-0 right-0 -->
  <footer
    class="flex flex-col lg:flex-row justify-between items-center w-full mx-auto pt-4 pb-8 border-t"
    v-for="item in content"
    v-if="content"
  >
    <h1 class="text-gray-500 text-center lg:text-left">
      {{ item.brand }}
      &copy;
      {{ currentYear }}
      {{ item.title }} -
      {{ item.body.children[0].children[0].value }}
    </h1>
    <div>
      <a
        :href="item.link"
        class="flex flex-row items-center text-blue-600 font-medium"
        target="_blank"
      >
        <IconFacebook class="w-10 h-fit p-2" />
        {{ item.linkText }}</a
      >
    </div>
  </footer>
</template>

<script lang="ts" setup>
import IconFacebook from "@/components/icons/IconFacebook.vue";
const currentYear = ref(new Date().getFullYear());

const { data: content } = await useAsyncData("footer", () => {
  return queryContent("/_partials/footer").where({ _partial: true }).find();
});
</script>
