<script setup lang="ts">
</script>
<template>
    <div class="top-bar">
        <ul>
          <li><a href="/">Home</a></li>
          <li><a href="/about">About</a></li>
        </ul>
    </div>
</template>
<style scoped lang="scss">
.top-bar {
    display: flex;
    justify-content: space-between; 
    align-items: center;
    background-color: lightgray;
    flex-direction: row-reverse;
    padding-right: $spacing-sm;
}

.top-bar ul {
  list-style: none;
  display: flex;
  gap: $spacing-sm;
}

.top-bar ul li a {
  text-decoration: none;
  color: $text-color;
}
</style>