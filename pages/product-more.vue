<template>
  <div class="min-h-screen bg-[#0D0B18] text-white flex flex-col items-center px-4 py-6 relative">
    <!-- Назад -->
    <button @click="closeWebApp" class="absolute top-4 left-4 text-white text-lg">← Назад</button>

    <!-- Стикер -->
    <div class="mt-16 mb-4 text-center product-more">
      <img src="@/assets/img/ak.png" class="w-24 h-24 mx-auto mb-2" alt="Sticker" />
      <h2 class="text-xl font-bold">Sticker</h2>
      <p class="text-sm text-gray-400">Bad News Eagles | Paris 2023</p>
    </div>

    <!-- Кнопки действий -->
    <div class="flex justify-around w-full mb-4">
      <button class="bg-[#1D1A2F] w-1/4 py-2 rounded-lg text-sm text-gray-500">продать</button>
      <NuxtLink to="/steam" class="bg-[#1D1A2F] w-1/4 py-2 rounded-lg text-sm text-gray-500">вывести</NuxtLink>
      <button class="bg-[#1D1A2F] w-1/4 py-2 rounded-lg text-sm text-gray-500">поделиться</button>
    </div>

    <!-- Таблица характеристик -->
    <div class="bg-[#1D1A2F] rounded-lg w-full text-sm overflow-hidden">
      <div class="flex border-b border-gray-700 p-2">
        <div class="w-1/2 text-gray-400">Владелец</div>
        <div class="w-1/2">🔵 Sarubola</div>
      </div>
      <div class="flex border-b border-gray-700 p-2">
        <div class="w-1/2 text-gray-400">Качество</div>
        <div class="w-1/2">—</div>
      </div>
      <div class="flex border-b border-gray-700 p-2">
        <div class="w-1/2 text-gray-400">Редкость</div>
        <div class="w-1/2">—</div>
      </div>
      <div class="flex border-b border-gray-700 p-2">
        <div class="w-1/2 text-gray-400">StatTrak</div>
        <div class="w-1/2">—</div>
      </div>
      <div class="flex border-b border-gray-700 p-2">
        <div class="w-1/2 text-gray-400">Цена</div>
        <div class="w-1/2">125 💠</div>
      </div>
      <div class="flex p-2">
        <div class="w-1/2 text-gray-400">Статус</div>
        <div class="w-1/2">получен в Steam</div>
      </div>
    </div>

    <!-- Закрыть -->
    <button @click="closeWebApp" class="w-full bg-[#F7D774] text-black py-3 rounded-lg font-semibold mb-6">
      Закрыть
    </button>
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
.product-more{
  width: 100%;
}
.product-more img{
  width: 80%;
  height: auto;
}
</style>