<template>
  <div class="border-4 border-blue-500">
    <header class="">
      <slot name="navigation">
        <AppNavigation :navigation-tree="navigation" />
      </slot>
    </header>
    <section class="bg-gray-200">
      <slot />
    </section>
    <footer class="">
      <AppFooter />
    </footer>
  </div>
</template>

<script setup>
const route = useRoute();
const { data: navigation } = await useAsyncData("navigation", () => {
  return fetchContentNavigation();
});
</script>

<style lang="scss" scoped>
div {
  content: "";
}
</style>
