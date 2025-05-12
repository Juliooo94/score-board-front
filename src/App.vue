<script setup lang="ts">
import TopBar from './components/TopBar.vue'
</script>

<template>
  <div id="app">
    <TopBar />
    <main class="content">
      <p>Main content goes here.</p>
    </main>
  </div>
</template>
<style scoped lang="scss">
#app {
  display: flex;
  flex-direction: column;
  min-height: 100vh;
  width: 100%;
}

.content {
  flex: 1;
  padding: $spacing-sm;
  background-color: #f4f4f4;
}
</style>
