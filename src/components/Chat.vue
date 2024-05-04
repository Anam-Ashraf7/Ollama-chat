<script>
import ollama from "ollama/browser";

export default {
  data() {
    return {
      isOllamaRunning: true,
      model: "",
      list: [],
      conversation: [{ prompt: "", response: "" }],
      newMessage: "",
    };
  },
  mounted() {
    this.getAvailableModels();
  },
  methods: {
    async getAvailableModels() {
      try {
        const models = await ollama.list();
        console.log(models);
        this.list = models.map((model) => model.name);
      } catch (error) {
        console.error("Error fetching available models:", error);
      }
      console.log(this.list)
    },
    async fetchResponse() {
      try {
        const response = await ollama.chat({
          model: "gemma:2b",
          messages: [
            {
              role: "user",
              content: this.conversation[this.conversation.length - 1].prompt,
            },
          ],
          stream: true,
        });

        for await (const part of response) {
          this.conversation[this.conversation.length - 1].response +=
            part.message.content;
        }
      } catch (error) {
        console.error("Error fetching response:", error);
        this.response = "Error: " + error.message;
      }
    },
    handleNewMessage() {
      if (this.newMessage.trim() !== "") {
        this.conversation.push({ prompt: this.newMessage, response: "" });
        this.fetchResponse();
        this.newMessage = ""; // Clear the input field
      }
    },
  },
};
</script>

<template>
  <div
    class="p-4 h-[calc(100vw-4rem)] w-full overflow-y-auto overflow-x-hidden"
  >
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
      <div class="flex flex-col gap-2 w-full">
        <div
          v-for="(item, index) in conversation"
          :key="index"
          class="flex flex-col gap-2 w-full"
        >
          <div class="chat chat-end">
            <span v-if="item.prompt" class="chat-bubble">{{
              item.prompt
            }}</span>
          </div>
          <div class="chat chat-start">
            <span v-if="item.response" class="chat-bubble">{{
              item.response
            }}</span>
          </div>
        </div>
      </div>
    </div>
  </div>
  <div class="p-4 flex justify-center gap-2">
    <input
      v-model="newMessage"
      type="text"
      placeholder="Message here..."
      class="input input-bordered w-full sticky bottom-0"
      @keyup.enter="handleNewMessage"
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
</div>
</template>

<style scoped></style>
