![Vuejs notion](https://github.com/TH-Activities/saturday-hack-night-template/assets/117498997/b879ba9f-2057-431b-99db-e86a0010b1ea)

# Ollama Chat

This repository houses the development of a chat UI designed specifically for [Ollama](https://ollama.com/), a powerful app to run large language model (LLM) capable of engaging in natural conversations on your device. The goal is to create a user-friendly interface that allows users to use Ollama effectively rather than relying on the command line interface.

## Team members

1. [Alwin Sunil](https://github.com/AlwinSunil)
2. [Mugilan S](https://github.com/mugilankani)
3. [Anam Ashraf](https://github.com/Anam-Ashraf7)

## Link to product walkthrough

[https://drive.google.com/file/d/1I-fLd7hF-lSWGvIXzAq0kCP9yWLLtEON/view?usp=sharing]

## How it Works ?

1. A chat UI for Ollama, enabling local use of large language models (LLMs) on your device seamless.
2. Provides an intuitive interface to interact with LLM's which are installed through Ollama.
3. Utilizes ollama-js library for seamless communication between UI and Ollama application providing a smooth user experience.

## Libraries used

- [Vue.js](https://vuejs.org/)
- [Vite](https://vitejs.dev/)
- [Tailwind CSS](https://tailwindcss.com/)
- [Ollama JS](https://github.com/ollama/ollama-js)

## How to Run

### Prerequisites

- Git (https://git-scm.com/)
- Node.js (https://nodejs.org/en)

### Installation of Ollama

- Install ollama on your device from [ollama.com](https://ollama.com/download)
- Download preferred model using ollama `ollama run llamm3`
- Replace `llama3` with the model you want to use, instructions are [here](https://github.com/ollama/ollama?tab=readme-ov-file#quickstart)

### Running Ollama Chat

Git clone the repository

`git clone https://github.com/Anam-Ashraf7/Strix`

Install dependencies
`npm install`

Start the development server
`npm run dev`

Go to http://localhost:5173/ to start using the chat UI.
