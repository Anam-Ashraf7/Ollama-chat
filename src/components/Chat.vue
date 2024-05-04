<template>
  <div class="flex flex-col w-full">
    <div class="flex flex-col items-center p-4 h-full w-2/3">
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
        Hey there! I'm Ollama, a chatbot that helps you with your tasks.
      </div>
    </div>
  </div>
  <div class="p-4 flex justify-center gap-2">
    <input
    type="text"
    placeholder="Message here..."
    class="input input-bordered w-2/3 sticky bottom-0"
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
