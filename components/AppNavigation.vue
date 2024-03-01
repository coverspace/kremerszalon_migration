<template>
  <div class="grid grid-col-12">
    <div class="col-span-12">
      <div class="flex flex-row justify-between items-center w-full">
        <NuxtLink to="/main">
          <NuxtImg src="logo.png" class="w-44 h-fit my-6" />
        </NuxtLink>
        <ul
          class="flex flex-row justify-end items-center gap-x-10 w-full p-4 px-8"
        >
          <li v-for="(item, index) in navigationTree" :key="index">
            <NuxtLink
              :to="item._path === '/main' ? '/' : item._path"
              class="font-bold text-lg pb-2"
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
const props = defineProps({
  navigationTree: {
    type: Array,
    default: () => [],
  },
});

onMounted(() => {
  // console.log("navigationTree", props.navigationTree);
});
</script>

<style lang="css" scoped>
.router-link-exact-active {
  border-bottom: 2px solid gray;
}

.router-link-exact-inactive {
  border-bottom: 2px solid transparent;
}
</style>
