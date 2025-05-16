<script setup lang="ts">
import { onMounted, ref } from 'vue';
import TopBar from './components/TopBar.vue';
const apiUrl = import.meta.env.VITE_API_URL;
const isLoggedIn = ref<boolean>(false);

onMounted(async () => {
  const res = await fetch(`${apiUrl}/user/me`, {
    method: "GET",
    headers: {
      "Content-Type": "application/json",
    },
    credentials: "include"
  })
  console.log(res)
  if (res.status == 200) {
    isLoggedIn.value = true
  }
})

</script>

<template>
  <div id="app">
    <TopBar :is-logged-in="isLoggedIn"/>
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
