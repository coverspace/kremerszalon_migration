<template>
  <button
    @click="scrollToTop"
    v-show="showButton"
    title="Lap tetejére"
    class="fixed bottom-5 right-0 z-10 p-2 rounded-l-lg border border-r-0 border-gray-300 bg-gray-100"
  >
    <IconUp class="w-5 h-auto text-gray-400 hover:text-gray-500" />
  </button>
</template>

<script setup>
import IconUp from "@/components/icons/IconUp.vue";
const showButton = ref(false);

// Function to scroll to the top of the page
const scrollToTop = () => {
  window.scrollTo({
    top: 0,
    behavior: "smooth",
  });
};

// Show the button when scrolling down
const handleScroll = () => {
  showButton.value = window.scrollY > 100; // Adjust the threshold as needed
};

// Listen for scroll events when the component is mounted
onMounted(() => {
  window.addEventListener("scroll", handleScroll);
});

// Remove the scroll event listener when the component is unmounted
onUnmounted(() => {
  window.removeEventListener("scroll", handleScroll);
});
</script>
