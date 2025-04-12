<template>
  <div class="h-screen flex flex-col justify-center items-center bg-gray-900 text-white">
    <h1 class="text-3xl font-bold mb-4">Telegram WebApp 🌐</h1>
    <p>User ID: {{ userId }}</p>
    <button @click="sendData" class="mt-4 bg-blue-600 px-4 py-2 rounded">
      Отправить данные боту
    </button>
  </div>
</template>

<script setup>
import { onMounted, ref } from 'vue'

const userId = ref('...')

onMounted(() => {
  const tg = window.Telegram.WebApp
  tg.expand()
  userId.value = tg.initDataUnsafe?.user?.id ?? 'не найден'
})

function sendData() {
  window.Telegram.WebApp.sendData("Данные от Nuxt Web App")
}
</script>
