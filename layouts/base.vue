<template>
  <div class="container mx-auto">
    <header class="">
      <slot name="navigation">
        <AppNavigation :navigation-tree="navigation" />
      </slot>
      <AppCarousel />
    </header>
    <section class="bg-white">
      <slot />
    </section>
    <footer class="mt-16">
      <AppFooter />
    </footer>
    <!-- partials -->
    <ScrollToTopButton />
  </div>
</template>

<script setup>
import ScrollToTopButton from "@/components/partials/ScrollToTopButton.vue";
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
