<template>
  <div class="min-h-screen bg-[#0D0B18] text-white flex flex-col items-center px-4 py-6 relative">
    <!-- Логотип -->
    <div class="my-6">
      <div
          class="w-24 h-24 rounded-full flex items-center justify-center text-4xl font-bold logo"
          :class="{ 'tapped': isTapped }"
          @click="handleTap"
      >
        <img src="~/assets/img/logo.png" alt="" />
      </div>
    </div>

    <!-- Название -->
    <h1 class="text-2xl font-bold mb-2">ULA BOX</h1>
    <p class="text-sm text-gray-300 text-center mb-6">
      Зарабатывай кристаллы и меняй их на кейсы, стикеры и скины для Counter Strike 2
    </p>

    <!-- Баланс -->
    <div class="bg-[#1D1A2F] w-full rounded-lg p-4 text-center mb-4">
      <div class="text-2xl font-semibold mb-1">💠 {{ balance }}</div>
      <p class="text-sm text-gray-400">Твой баланс</p>
      <p class="text-xs text-gray-500 mt-1">Осталось нажатий: {{ 100 - tapCount }}</p>
    </div>

    <!-- Кнопка -->
    <button class="w-full bg-[#F7D774] text-black py-3 rounded-lg font-semibold mb-6">
      Купить кристаллы
    </button>

    <!-- Задания -->
    <div class="w-full">
      <h2 class="text-sm font-semibold mb-2">Задания</h2>

      <div class="bg-[#1D1A2F] rounded-lg p-4 mb-3">
        <p class="text-sm font-medium mb-2">Подписаться на канал</p>
        <div class="flex items-center justify-between">
          <span class="text-sm text-gray-400">+500 💠</span>
          <button class="bg-[#F7D774] text-black px-4 py-1 rounded-md text-sm font-medium">Подписаться</button>
        </div>
      </div>

      <div class="bg-[#1D1A2F] rounded-lg p-4">
        <p class="text-sm font-medium mb-2">Подписаться на канал</p>
        <div class="flex items-center justify-between">
          <span class="text-sm text-gray-400">+500 💠</span>
          <button class="bg-[#F7D774] text-black px-4 py-1 rounded-md text-sm font-medium">Подписаться</button>
        </div>
      </div>
    </div>
  </div>
</template>
<script setup>
import { ref, onMounted } from 'vue'

const balance = ref(0)
const tapCount = ref(0)
const isTapped = ref(false)

function handleTap() {
  if (tapCount.value >= 100) return

  tapCount.value++
  balance.value++

  isTapped.value = true
  setTimeout(() => (isTapped.value = false), 150)

  saveToLocalStorage()
}

function saveToLocalStorage() {
  const data = {
    balance: balance.value,
    tapCount: tapCount.value,
    timestamp: Date.now()
  }
  localStorage.setItem('tapStats', JSON.stringify(data))
}

function loadFromLocalStorage() {
  const data = JSON.parse(localStorage.getItem('tapStats'))
  if (!data) return

  const now = Date.now()
  const diff = now - data.timestamp
  const oneDay = 24 * 60 * 60 * 1000

  if (diff >= oneDay) {
    tapCount.value = 0
    balance.value = data.balance
  } else {
    balance.value = data.balance
    tapCount.value = data.tapCount
  }
}

onMounted(() => {
  loadFromLocalStorage()
})
</script>
<style scoped>
.logo {
  width: 250px;
  height: 250px;
  transition: transform 0.1s ease;
}
.logo.tapped {
  transform: scale(0.85);
}
.logo img {
  width: 100%;
}
</style>
