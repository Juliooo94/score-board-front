<script setup lang="ts">
import { onMounted, ref } from 'vue'

const message = ref('Loading...')


onMounted(async () => {
  try {
    const res = await fetch('http://localhost:8000')
    const data = await res.json()
    message.value = data.message
  } catch (error) {
    message.value = 'Failed to fetch message'
  }
})
</script>

<template>
  <div class="card">
    <p>
      {{ message }}
    </p>
  </div>
</template>

<style scoped>
</style>
