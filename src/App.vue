<template>
  <div class="container p-4 mx-auto">
    <h1 class="text-2xl">Coin Market</h1>

    <Search v-model="textSearch" />

    <Table :titles="titles" :coins="searchCoin" />
  </div>
</template>

<script setup>
import { computed, onBeforeMount, ref } from "vue";
import Search from "./components/Search.vue";
import Table from "./components/Table.vue";

import { fetchCoins } from "./service/coinGecko";

const coins = ref([]);
const titles = ref(["#", "Coin", "Price", "Price Change", "24h Volume"]);
const textSearch = ref("");

onBeforeMount(async () => {
  coins.value = await fetchCoins();
});

const searchCoin = computed(() => {
  return coins.value.filter(
    (coin) =>
      coin.name.toLowerCase().includes(textSearch.value.toLowerCase()) ||
      coin.symbol.toLowerCase().includes(textSearch.value.toLowerCase())
  );
});
</script>
