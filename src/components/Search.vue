<template>
  <input
    type="text"
    class="
      bg-gray-200
      border-gray-700
      text-white
      border-2
      my-4
      p-2
      rounded-lg
      w-full
    "
    placeholder="Search Coin"
    :value="modelValue"
    @input="$emit('update:modelValue', $event.target.value)"
  />
</template>

<script setup>
const props = defineProps({
  modelValue: { type: String },
});
</script>
