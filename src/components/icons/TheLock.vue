
<template>
  <svg class="lock" xmlns="http://www.w3.org/2000/svg" width="28px" height="28px" viewBox="0 0 24 24">
    <path fill="currentColor" fillRule="evenodd" v-if="!isLocked"
      d="M6.75 8a5.25 5.25 0 0 1 10.335-1.313a.75.75 0 0 0 1.452-.374A6.75 6.75 0 0 0 5.25 8v2.055c-1.115.083-1.84.293-2.371.824C2 11.757 2 13.172 2 16c0 2.828 0 4.243.879 5.121C3.757 22 5.172 22 8 22h8c2.828 0 4.243 0 5.121-.879C22 20.243 22 18.828 22 16c0-2.828 0-4.243-.879-5.121C20.243 10 18.828 10 16 10H8c-.452 0-.867 0-1.25.004V8ZM14 16a2 2 0 1 1-4 0a2 2 0 0 1 4 0Z"
      clipRule="evenodd"></path>

    <path v-else fill="currentColor" fill-rule="evenodd"
      d="M5.25 10.055V8a6.75 6.75 0 0 1 13.5 0v2.055c1.115.083 1.84.293 2.371.824C22 11.757 22 13.172 22 16c0 2.828 0 4.243-.879 5.121C20.243 22 18.828 22 16 22H8c-2.828 0-4.243 0-5.121-.879C2 20.243 2 18.828 2 16c0-2.828 0-4.243.879-5.121c.53-.531 1.256-.741 2.371-.824ZM6.75 8a5.25 5.25 0 0 1 10.5 0v2.004C16.867 10 16.451 10 16 10H8c-.452 0-.867 0-1.25.004V8ZM14 16a2 2 0 1 1-4 0a2 2 0 0 1 4 0Z"
      clip-rule="evenodd" />

  </svg>
</template>

<script setup lang="ts">
defineProps({
  isLocked: { type: Boolean, required: true }
})

</script>

<style scoped>
.lock {
  margin-left: 14px;
}

.lock:hover {
  color: rgb(179, 168, 168);
  cursor: pointer;
}
</style>