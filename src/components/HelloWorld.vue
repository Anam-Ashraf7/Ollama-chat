<script setup>
import { ref } from "vue";

defineProps({
  msg: String,
});

const count = ref(0);
</script>

<template>
  <h1 class="text-red-600 text-3xl">{{ msg }}</h1>
</template>

<style></style>
