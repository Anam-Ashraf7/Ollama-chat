<script>
import ollama from "ollama/browser";

export default {
  data() {
    return {
      response: "",
      prompt: "What is your name?",
    };
  },
  mounted() {
    this.fetchResponse();
  },
  methods: {
    async fetchResponse() {
      try {
        const message = { role: "user", content: this.prompt };
        const response = await ollama.chat({
          model: "gemma:2b",
          messages: [message],
          stream: true,
        });
        for await (const part of response) {
          this.response += part.message.content;
        }
      } catch (error) {
        console.error("Error:", error);
      }
    },
  },
};
</script>

<template>
  <div class="p-4 h-full w-full">
    <div class="chat chat-start">
      <div class="chat-image avatar">
        <div class="w-10 rounded-full">
          <img
            class="bg-white !object-contain"
            alt="Tailwind CSS chat bubble component"
            src="https://ollama.com/public/ollama.png"
          />
        </div>
      </div>
      <div class="chat-bubble">
        {{ response }}
      </div>
    </div>
  </div>
  <div class="p-4 flex gap-2">
    <input
      type="text"
      placeholder="Message here..."
      class="input input-bordered w-full sticky bottom-0"
    />

    <button class="btn btn-primary">
      <svg
        xmlns="http://www.w3.org/2000/svg"
        width="24"
        height="24"
        viewBox="0 0 24 24"
        fill="none"
        stroke="currentColor"
        stroke-width="2"
        stroke-linecap="round"
        stroke-linejoin="round"
        class="lucide lucide-send-horizontal"
      >
        <path d="m3 3 3 9-3 9 19-9Z" />
        <path d="M6 12h16" />
      </svg>
    </button>
  </div>
</template>

<style scoped></style>
