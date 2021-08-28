<template>
  <table class="text-white w-full">
    <thead>
      <tr class="font-bold text-lg bg-gray-800">
        <th class="p-2" v-for="title in titles" :key="title">
          {{ title }}
        </th>
      </tr>
    </thead>

    <tbody>
      <tr
        class="text-center bg-gray-700"
        v-for="(coin, index) in coins"
        :key="coin.id"
      >
        <td class="text-gray-400 p-2">{{ index + 1 }}</td>

        <td class="flex items-center p-2 space-x-4">
          <img :src="coin.image" :alt="coin.name" class="w-8" />

          <span>
            {{ coin.name }}
          </span>

          <span class="text-gray-400">
            {{ coin.symbol }}
          </span>
        </td>

        <td class="p-2">$ {{ coin.current_price }}</td>

        <td
          class="p-2"
          :class="[
            coin.price_change_percentage_24h > 0
              ? 'text-green-600'
              : 'text-red-600',
          ]"
        >
          {{ coin.price_change_percentage_24h }} %
        </td>

        <td class="p-2">$ {{ coin.total_volume.toLocaleString() }}</td>
      </tr>
    </tbody>
  </table>
</template>

<script setup>
const props = defineProps({
  coins: { type: Array },
  titles: { type: Array },
});
</script>
