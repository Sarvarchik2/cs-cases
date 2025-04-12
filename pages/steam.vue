<template>
  <div class="min-h-screen bg-[#0D0B18] text-white px-4 pt-6 pb-24 relative">
    <!-- Header -->
    <NuxtLink to="/" class="absolute top-4 left-4 text-white text-lg z-10">✕ Назад</NuxtLink>

    <!-- Icon -->
    <div class="flex flex-col items-center mt-10 mb-6 ">
      <img src="@/assets/img/duck-steam.png" class="w-20 mb-4" />
      <h1 class="text-xl font-bold text-center mb-2">Куда отправлять предметы?</h1>
      <p class="text-sm text-gray-400 text-center px-2">
        Кейсы, стикеры и наклейки отправляются с помощью ссылки обмена. Найди свою ссылку обмена на странице обмена в Steam
      </p>
    </div>

    <!-- Input -->
    <div class="bg-[#1D1A2F] rounded-lg px-4 py-3 mb-6 steam-input">
      <input
          class="w-full bg-transparent text-sm text-blue-400 placeholder-gray-500 focus:outline-none"
          placeholder="вставьте ссылку на ваш инвентарь"
          type="text"
      />
    </div>

    <!-- Button -->
    <button class="w-full bg-[#F7D774] text-black py-3 rounded-lg font-semibold">
      Сохранить
    </button>
  </div>
</template>

<script setup>
</script>

<style scoped>
.steam-input{
  height: 120px;
}
</style>