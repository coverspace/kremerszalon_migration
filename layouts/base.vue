<template>
  <div class="lg:container mx-auto">
    <header class="">
      <CreditCards />
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
    <CookieBanner />
  </div>
</template>

<script setup>
import CreditCards from "@/components/partials/CreditCards.vue";
import ScrollToTopButton from "@/components/partials/ScrollToTopButton.vue";
import CookieBanner from "@/components/partials/CookieBanner.vue";
const route = useRoute();
const { data: navigation } = await useAsyncData("navigation", () => {
  return fetchContentNavigation();
});
</script>

<style lang="css" scoped>
body {
  background-color: white;
}
</style>
