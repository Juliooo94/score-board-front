<script setup lang="ts">
import { ref } from 'vue';
import LoginFrom from './LoginForm.vue';
defineProps({
  isLoggedIn: Boolean,
});
let showLogin = ref<boolean>(false)
</script>

<template>
   <button class="login-button" @click="showLogin=!showLogin" :disabled="isLoggedIn"><i class=" icon fa-regular fa-circle-user fa-lg"></i></button>
   <div 
      v-if="showLogin"
      class="popup-container"
    >
      <LoginFrom />
    </div>

</template>

<style scoped lang="scss">
.login-button {
  aspect-ratio: 1;
  border-radius: 50%;
  display: grid;
  place-items: center;
  padding: $spacing-sm;
  position: relative;
}
.popup-container {
  position: absolute;
  right: 0;
  padding: $spacing-sm;
  margin: $spacing-xs;
  background: white;
  border-radius: $spacing-xs;
}
</style>
