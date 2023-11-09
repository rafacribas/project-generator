<script setup lang="ts">
import { RouterView } from 'vue-router'
</script>

<template>
  <header style="display: flex; justify-content: center">
    <h1>Vue Project Generator</h1>
  </header>

  <RouterView />
</template>

<style scoped>
h1 {
  font-size: 64px;
}
</style>
