<template>
  <div class="grid grid-col-12">
    <div class="col-span-12">
      <div
        class="flex flex-col justify-center items-center border-2 border-red-500 my-2"
      >
        <ContentDoc path="/contact/block_02" v-slot="{ doc }">
          <div class="text-center lg:text-left">
            <h1 class="text-center">{{ doc.button }}</h1>
            <ContentRenderer :value="doc" />
          </div>
        </ContentDoc>
      </div>
    </div>
  </div>
</template>
