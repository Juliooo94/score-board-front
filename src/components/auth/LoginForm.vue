<script setup lang="ts">
import { ref } from 'vue';

defineProps({
  isShown: Boolean
});

const username = ref<string>('')
const password = ref<string>('')
const error = ref<string>('')
const apiUrl = import.meta.env.VITE_API_URL;
const emit = defineEmits(['update:isShown']);

async function login(): Promise<void> {
  // I keep the api call here cause I will soon use Vue Query and I prefere to do this quickly
  const res = await fetch(`${apiUrl}/user/login`, {
    method: "POST",
    headers: {
      "Content-Type": "application/json",
    },
    body: JSON.stringify({username: username.value, password: password.value})
  })
  if (res.status == 200) {
    emit('update:isShown', false)
  } else {
    const response = await res.json()
    error.value = response.error
  }
}
</script>
<template>
  <div class="container">
    <form @submit.prevent="login" class="form">
      <input v-model="username" type="text" placeholder="Username" class="input" />
      <input v-model="password" type="password" placeholder="Password" class="input" />
      <button type="submit" class="button" :disabled="!username || !password">Login or Register</button>
      <span v-if="error" class="error">{{ error }}</span>
    </form>
  </div>
</template>
<style scoped lang="scss">
.container {
    display: flex;
    flex-direction: column;
    gap: $spacing-xs;
    width: 100%;
    max-width: 170px;
}
.form {
    display: flex;
    flex-direction: column;
    gap: $spacing-xs;
}
.input {
    border-radius: $spacing-xs;
    outline: 4px auto #b0b0b0;
}
.button {
    height:fit-content;
}
.error {
  color: red;
  word-break: break-word;
  overflow-wrap: break-word;
  min-height: 1.5em;
}
</style>