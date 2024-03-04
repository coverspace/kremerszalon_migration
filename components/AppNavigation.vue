<template>
  <div class="grid grid-cols-12">
    <div class="col-span-12">
      <div class="lg:hidden flex flex-row justify-between items-center">
        <a href="/">
          <NuxtImg src="logo.png" class="w-44 h-fit my-6 mx-4" />
        </a>
        <button @click="openMenu">
          <IconMenu
            class="w-16 h-fit p-2 border rounded-lg mx-6 bg-gray-100 text-gray-500"
          />
        </button>
      </div>
      <SideBar :setBar="setBar" @cancel="setBar = false" />
      <div class="hidden lg:flex flex-row justify-between items-center w-full">
        <a href="/">
          <NuxtImg src="logo.png" class="w-44 h-fit my-6 mx-4" />
        </a>
        <ul
          class="flex flex-row justify-end items-center gap-x-10 w-full p-4 px-8"
        >
          <li v-for="(item, index) in navigationTree" :key="index">
            <NuxtLink
              :to="item._path === '/main' ? '/' : item._path"
              class="text-gray-600 font-bold text-xl pb-2"
            >
              {{ item.children[0].title }}
            </NuxtLink>
          </li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script setup>
import IconMenu from "@/components/icons/IconMenu.vue";
import SideBar from "@/components/partials/SideBar.vue";
const props = defineProps({
  navigationTree: {
    type: Array,
    default: () => [],
  },
});

const setBar = ref(false);

onMounted(() => {
  // console.log("navigationTree", props.navigationTree);
});

const openMenu = () => {
  console.log("openMenu");
  setBar.value = !setBar.value;
};
</script>

<style lang="css" scoped>
.router-link-exact-active {
  border-bottom: 2px solid gray;
}

.router-link-exact-inactive {
  border-bottom: 2px solid transparent;
}
</style>
