<script setup>
const model = defineModel();

defineProps({
  background: String,
  foreground: String
});
</script>

<template>
  <label class="size-10 rounded-full shadow-md" :style="{'background-color': background, color}">
    <input v-model="model" type="radio" class="hidden" v-bind="$attrs"></input>
  </label>
</template>
