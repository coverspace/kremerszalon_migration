<template>
  <div
    v-show="setBar"
    class="opacity-100 absolute top-0 right-0 z-10 w-3/4 h-full overflow-hidden border border-gray-100 bg-gradient-to-r from-cyan-100 to-zinc-100"
  >
    <div class="flex flex-col justify-start items-start w-full">
      <button @click="$emit('cancel')" class="ml-auto mr-0 p-5">
        <IconClose
          class="w-16 h-fit text-gray-500 border-2 rounded-lg bg-slate-100"
        />
      </button>
      <h1>Oldalsáv menü</h1>
    </div>
  </div>
</template>

<script setup>
import IconClose from "@/components/icons/IconClose.vue";

const props = defineProps({
  setBar: {
    type: Boolean,
  },
});

const emit = defineEmits(["cancel"]);

onMounted(() => {
  console.log("mounted");
});
</script>
