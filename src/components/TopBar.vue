<script setup lang="ts">
import Authentication from './auth/Authentication.vue';
defineProps({
  isLoggedIn: Boolean,
});
</script>
<template>
    <div class="top-bar">
        <ul>
          <li><Authentication :is-logged-in="isLoggedIn"/></li>
        </ul>
    </div>
</template>
<style scoped lang="scss">
.top-bar {
    display: flex;
    justify-content: space-between; 
    background-color: rgb(219, 214, 214);
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