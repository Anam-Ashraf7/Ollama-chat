<script>
import ollama from "ollama/browser";

export default {
  emits: ["modelSelected"], // Declare the event
  data() {
    return {
      list: [],
      isDropdownOpen: false, // Add a data property to track the dropdown state
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
        this.list.push(modelName);
      }
      console.log(this.list);
    },
    selectModel(model) {
      this.$emit("modelSelected", model); // Emit the event with the selected model
      this.isDropdownOpen = false; // Close the dropdown
    },
    toggleDropdown() {
      this.isDropdownOpen = !this.isDropdownOpen; // Toggle the dropdown state
    },
  },
};
</script>
<template>
  <!-- <div> -->
  <div class="navbar bg-base-100">
    <div class="flex-none">
      <a
        href="https://github.com/Anam-Ashraf7/Strix?tab=readme-ov-file#how-to-run"
        target="_blank"
        rel="noopener noreferrer"
      >
        <button class="btn btn-square btn-ghost">
          <svg
            xmlns="http://www.w3.org/2000/svg"
            height="24px"
            viewBox="0 -960 960 960"
            width="24px"
            fill="#e8eaed"
          >
            <path
              d="M480-280q17 0 28.5-11.5T520-320v-160q0-17-11.5-28.5T480-520q-17 0-28.5 11.5T440-480v160q0 17 11.5 28.5T480-280Zm0-320q17 0 28.5-11.5T520-640q0-17-11.5-28.5T480-680q-17 0-28.5 11.5T440-640q0 17 11.5 28.5T480-600Zm0 520q-83 0-156-31.5T197-197q-54-54-85.5-127T80-480q0-83 31.5-156T197-763q54-54 127-85.5T480-880q83 0 156 31.5T763-763q54 54 85.5 127T880-480q0 83-31.5 156T763-197q-54 54-127 85.5T480-80Zm0-80q134 0 227-93t93-227q0-134-93-227t-227-93q-134 0-227 93t-93 227q0 134 93 227t227 93Zm0-320Z"
            />
          </svg>
        </button>
      </a>
    </div>
    <div class="flex-1">
      <a class="btn btn-ghost text-xl">Ollama Chat</a>
    </div>
    <div class="flex-none">
      <div class="dropdown dropdown-bottom dropdown-end mr-5">
        <button tabindex="0" role="button" class="btn btn-square btn-ghost">
          <svg
            xmlns="http://www.w3.org/2000/svg"
            fill="none"
            viewBox="0 0 24 24"
            class="inline-block w-5 h-5 stroke-current"
          >
            <path
              stroke-linecap="round"
              stroke-linejoin="round"
              stroke-width="2"
              d="M5 12h.01M12 12h.01M19 12h.01M6 12a1 1 0 11-2 0 1 1 0 012 0zm7 0a1 1 0 11-2 0 1 1 0 012 0zm7 0a1 1 0 11-2 0 1 1 0 012 0z"
            ></path>
          </svg>
        </button>
        <ul
          tabindex="0"
          class="dropdown-content z-[1] menu p-2 shadow bg-base-100 rounded-box w-52"
        >
          <li v-for="model in list" :key="model">
            <a @click="selectModel(model)">{{ model }}</a>
          </li>
        </ul>
      </div>
    </div>
  </div>
</template>
