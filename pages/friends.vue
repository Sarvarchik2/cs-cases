<template>
  <div class="min-h-screen bg-[#0D0B18] text-white px-4 pt-6 pb-24 relative">
    <!-- Header -->
    <NuxtLink to="/" class="absolute top-4 left-4 text-white text-lg z-10">✕ Назад</NuxtLink>


    <!-- Title -->
    <div class="text-center mb-6">
      <img src="@/assets/img/invite-icon.png" class="w-20 mx-auto mb-4" />
      <h1 class="text-xl font-bold">Приглашай друзей и получай кристаллы</h1>
    </div>

    <!-- Friends List -->
    <div class="mb-4 text-sm text-gray-400">0 Друга</div>
    <div class="space-y-3 mb-6">
      <div class="flex items-center justify-between bg-[#1D1A2F] p-3 rounded-lg">
        <div>
          <p class="font-medium">Журабаев Асадбек</p>
          <p class="text-xs text-gray-400">320 коинов, 4 предмет</p>
        </div>
        <div class="text-right">
          <p class="text-sm">+500 💠</p>
        </div>
      </div>

      <div class="flex items-center justify-between bg-[#1D1A2F] p-3 rounded-lg">
        <div>
          <p class="font-medium">Хокимов Акбар</p>
          <p class="text-xs text-gray-400">320 коинов, 4 предмет</p>
        </div>
        <div class="text-right">
          <p class="text-sm">+500 💠</p>
        </div>
      </div>

      <div class="flex items-center justify-between bg-[#1D1A2F] p-3 rounded-lg">
        <div>
          <p class="font-medium">Трейдеров Бехруз</p>
          <p class="text-xs text-gray-400">320 коинов, 4 предмет</p>
        </div>
        <div class="text-right">
          <p class="text-sm">+500 💠</p>
        </div>
      </div>
    </div>

    <!-- Invite Button -->
    <button class="w-full bg-[#F7D774] text-black py-3 rounded-lg font-semibold flex items-center justify-center gap-2">
      Пригласить друга <span class="text-sm">💠 500</span>
    </button>

    <!-- Навигация -->

  </div>
</template>

<script setup>
</script>

<style scoped>
</style>