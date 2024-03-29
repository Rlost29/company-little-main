<script setup lang="ts">
import { RouterLink, RouterView } from 'vue-router'
import { ref } from 'vue'
const open = ref(false)
import headervue from './components/header.vue'
</script>

<template>
  <headervue />
  <RouterView />
</template>
