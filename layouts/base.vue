<template>
  <div class="container mx-auto">
    <header class="">
      <slot name="navigation">
        <AppNavigation :navigation-tree="navigation" />
      </slot>
      <AppCarousel />
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

<style lang="css" scoped>
body {
  background-color: red;
}
</style>
