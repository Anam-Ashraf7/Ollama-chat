<script>
import ollama from "ollama/browser";

export default {
  data() {
    return {
      list: [],
    };
  },
  mounted() {
    this.getAvailableModels();
  },
  methods: {
    async getAvailableModels() {
      const models = await ollama.list();
      console.log(models);
      for (let i = 0, j = models.models.length; i < j; i++) {
        const modelName = models.models[i].name;
        const separatedName = modelName.split(":");
        this.list.push(separatedName[0]);
      }
      console.log(this.list);
    },
  },
};
</script>

<template>
  <!-- <div> -->
  <div class="navbar bg-base-200">
    <div class="flex-1 items-center bg-base">
      <div class="px-3 chat-image avatar">
          <div class="w-10 rounded-full">
            <img
            class="bg-white !object-contain"
            alt="Tailwind CSS chat bubble component"
            src="https://ollama.com/public/ollama.png"
            />
        </div>
      </div>
      <a class="text-xl">Ollama Chat</a>
    </div>
    <div class="flex-none">
      <div class="dropdown dropdown-bottom dropdown-end mr-5">
        <div tabindex="0" role="button" class="flex btn btn-ghost">
          Models 
          <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="lucide lucide-chevron-down"><path d="m6 9 6 6 6-6"/></svg>
        </div>
    <ul
      tabindex="0"
      class="dropdown-content z-[1] menu p-2 shadow bg-base-200 rounded-box w-52"
    >
      <li v-for="model in list" :key="model">
        <a>{{ model }}</a>
      </li>
    </ul>
    </div>
    </div>
  </div>
  <!-- </div> -->
</template>