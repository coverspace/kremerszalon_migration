<template>
  <div class="grid grid-cols-12">
    <div class="col-span-12 my-8">
      <div class="flex flex-col justify-center items-center">
        <ContentDoc path="prices/block_01" v-slot="{ doc }">
          <h1
            class="flex flex-row justify-start items-center my-8 text-gray-600 text-xl mx-auto lg:text-4xl mt-2 lg:ml-0 lg:mr-auto"
          >
            <IconWallet class="w-8 h-fit" />
            {{ doc.prices_title }}
          </h1>
          <div
            class="flex flex-col lg:flex-row flex-wrap justify-start items-between h-full"
          >
            <div
              v-for="tables in doc.price_table"
              :key="tables.row"
              class="flex flex-row justify-start items-start w-full lg:w-1/2 p-4"
            >
              <div
                v-for="rows of tables"
                :key="tables.row"
                class="px-8 py-6 w-full rounded-lg shadow-lg bg-gradient-to-r from-amber-100 to-zinc-100"
              >
                <ul v-for="row in rows" :key="row.type">
                  <li v-for="(item, index) in row" :key="index">
                    <p
                      v-if="item.type && item.price"
                      class="flex flex-row justify-between items-center text-lg text-gray-500"
                    >
                      <span class="font-medium">{{ item.type }}</span>
                      <span class="font-bold">{{ item.price }}</span>
                    </p>
                    <h1 v-else class="text-xl font-semibold text-gray-600 mb-4">
                      {{ item }}
                    </h1>
                  </li>
                </ul>
              </div>
            </div>
          </div>
          <small class="mt-4 text-gray-500 text-base font-light">{{
            doc.tax
          }}</small>
        </ContentDoc>
      </div>
    </div>
  </div>
</template>

<script setup>
import IconWallet from "@/components/icons/IconWallet.vue";
</script>
