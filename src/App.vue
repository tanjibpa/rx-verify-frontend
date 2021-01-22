<template>
  <div>
    <nav class="bg-gray-800">
      <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
        <div class="flex items-center justify-between h-16">
          <div class="flex items-center">
            <div class="flex-shrink-0">
              <h1 class="font-sans font-black text-gray-50">Medicine Verification</h1>
            </div>
          </div>
        </div>
      </div>
    </nav>
    <SearchBatch />
  </div>
</template>

<script setup>
import SearchBatch from "./components/SearchBatch.vue";
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  background: rgba(110, 231, 183, var(--tw-bg-opacity));
}
</style>
