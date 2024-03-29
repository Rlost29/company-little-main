<script setup lang="ts">
import { ref } from 'vue'
const open = ref(false)
import { RouterLink } from 'vue-router'
</script>

<template>
  <header class="sticky top-0 z-50 bg-white">
    <nav class="container relative flex items-center justify-between px-6 py-8 mx-auto">
      <a href="#">
        <svg
          xmlns="http://www.w3.org/2000/svg"
          class="w-8 h-8 md:w-10 md:h-10"
          fill="none"
          viewBox="0 0 24 24"
          stroke="currentColor"
          stroke-width="2"
        >
          <path
            stroke-linecap="round"
            stroke-linejoin="round"
            d="M4 5a1 1 0 011-1h14a1 1 0 011 1v2a1 1 0 01-1 1H5a1 1 0 01-1-1V5zM4 13a1 1 0 011-1h6a1 1 0 011 1v6a1 1 0 01-1 1H5a1 1 0 01-1-1v-6zM16 13a1 1 0 011-1h2a1 1 0 011 1v6a1 1 0 01-1 1h-2a1 1 0 01-1-1v-6z"
          />
        </svg>
      </a>

      <button @click="open = !open" class="md:hidden">
        <span v-show="!open">
          <svg
            xmlns="http://www.w3.org/2000/svg"
            class="w-6 h-6"
            fill="none"
            viewBox="0 0 24 24"
            stroke="currentColor"
            stroke-width="2"
          >
            <path stroke-linecap="round" stroke-linejoin="round" d="M4 6h16M4 12h16m-7 6h7" />
          </svg>
        </span>

        <span v-show="open">
          <svg
            xmlns="http://www.w3.org/2000/svg"
            class="w-5 h-5"
            viewBox="0 0 20 20"
            fill="currentColor"
          >
            <path
              fill-rule="evenodd"
              d="M4.293 4.293a1 1 0 011.414 0L10 8.586l4.293-4.293a1 1 0 111.414 1.414L11.414 10l4.293 4.293a1 1 0 01-1.414 1.414L10 11.414l-4.293 4.293a1 1 0 01-1.414-1.414L8.586 10 4.293 5.707a1 1 0 010-1.414z"
              clip-rule="evenodd"
            />
          </svg>
        </span>
      </button>

      <div
        :class="[open ? 'translate-x-0 opacity-100 ' : 'opacity-0 -translate-x-full']"
        class="absolute inset-x-0 z-30 w-full px-6 py-8 mt-4 space-y-6 transition-all duration-300 ease-in-out bg-white top-16 md:mt-0 md:p-0 md:top-0 md:relative md:bg-transparent md:w-auto md:opacity-100 md:translate-x-0 md:space-y-0 md:-mx-6 md:flex md:items-center"
      >
        <router-link
          to="/"
          class="block transition-colors duration-300 md:px-6 hover:text-indigo-300"
        >
          Home</router-link
        >
        <router-link
          to="/about"
          class="block transition-colors duration-300 md:px-6 hover:text-indigo-300"
        >
          About</router-link
        >
        <router-link
          to="/service"
          class="block transition-colors duration-300 md:px-6 hover:text-indigo-300"
        >
          Service</router-link
        >
        <router-link
          to="/teams"
          class="block transition-colors duration-300 md:px-6 hover:text-indigo-300"
        >
          Teams</router-link
        >
      </div>
    </nav>
  </header>
</template>
