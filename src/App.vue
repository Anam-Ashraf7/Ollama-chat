<script setup>
import { ref } from "vue";
import Chat from "./components/Chat.vue";
import Navbar from "./components/Navbar.vue";

const selectedModel = ref("");

const handleModelSelected = (model) => {
  selectedModel.value = model;
};
</script>

<template>
  <Navbar @modelSelected="handleModelSelected" />
  <Chat :model="selectedModel" />
</template>
