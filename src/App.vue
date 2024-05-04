<script setup>
import Chat from "./components/Chat.vue";
import Navbar from "./components/Navbar.vue";
import SideBar from "./components/SideBar.vue";
</script>

<template>
  <Navbar />
  <div class="flex h-full">
    <SideBar/>
    <Chat />
  </div>
</template>
