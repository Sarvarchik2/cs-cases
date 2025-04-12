<template>
  <div class="min-h-screen bg-[#0D0B18] text-white flex flex-col items-center px-4 py-6 relative">
    <!-- Закрыть -->
    <button @click="closeWebApp" class="absolute top-4 left-4 text-white text-lg">✕ Закрыть</button>

    <!-- Логотип -->
    <div class="my-6">
      <div class="w-24 h-24 rounded-full bg-gradient-to-tr from-gray-300 to-white flex items-center justify-center text-4xl font-bold shadow-lg">
        <img class="w-16 h-16" src="~/assets/img/logo.png" alt="" />
      </div>
    </div>

    <!-- Название -->
    <h1 class="text-2xl font-bold mb-2">ULA BOX</h1>
    <p class="text-sm text-gray-300 text-center mb-6">
      Зарабатывай кристаллы и меняй их на кейсы, стикеры и скины для Counter Strike 2
    </p>

    <!-- Баланс -->
    <div class="bg-[#1D1A2F] w-full rounded-lg p-4 text-center mb-4">
      <div class="text-2xl font-semibold mb-1">💠 777</div>
      <p class="text-sm text-gray-400">Твой баланс</p>
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

    <!-- Навигация -->

  </div>
</template>

<script setup>
function closeWebApp() {
  if (window?.Telegram?.WebApp?.close) {
    window.Telegram.WebApp.close()
  }
}
</script>

<style scoped>
</style>