<template>
  <div class="min-h-screen bg-[#0D0B18] text-white px-4 pt-6 pb-24 relative">
    <!-- Header -->
    <NuxtLink to="/" class="absolute top-4 left-4 text-white text-lg z-10">✕ Назад</NuxtLink>

    <!-- Avatar & Name -->
    <div class="flex flex-col items-center mt-8 mb-6">
      <img :src="user?.photo_url || Avatar" class="w-24 h-24 rounded-full mb-2" alt="Avatar" />
      <p class="text-lg font-semibold">{{ user?.first_name }} {{ user?.last_name }}</p>
    </div>

    <!-- Trade Link -->
    <NuxtLink to="/steam" class="flex items-center justify-between bg-[#1D1A2F] px-4 py-3 rounded-lg mb-6">
      <div to="/steam" class="flex items-center gap-2">
        <span class="text-yellow-400">🔗</span>
        <span class="text-sm">Ссылка обмена</span>
      </div>
      <span class="text-white">›</span>
    </NuxtLink>

    <!-- Top 3 Items -->
    <h2 class="text-sm text-gray-300 mb-2">ТОП 3 предмета</h2>
    <div class="grid grid-cols-3 gap-3 mb-6">
      <div class="bg-[#1D1A2F] rounded-lg p-2 text-center text-xs border-b-4 border-red-600">
        <img src="~/assets/img/ak.png" class="mx-auto mb-1" />
        <p>AK-47</p>
        <p class="text-gray-400">Asimov</p>
      </div>
      <div class="bg-[#1D1A2F] rounded-lg p-2 text-center text-xs border-b-4 border-red-600">
        <img src="~/assets/img/ak.png" class="mx-auto mb-1" />
        <p>AK-47</p>
        <p class="text-gray-400">Asimov</p>
      </div>
      <div class="bg-[#1D1A2F] rounded-lg p-2 text-center text-xs border-b-4 border-red-600">
        <img src="~/assets/img/ak.png" class="mx-auto mb-1" />
        <p>AK-47</p>
        <p class="text-gray-400">Asimov</p>
      </div>
    </div>

    <!-- Withdrawn -->
    <h2 class="text-sm text-gray-300 mb-2">Выведено</h2>
    <div class="grid grid-cols-3 gap-3 mb-6">
      <NuxtLink to="/product-more" class="bg-[#1D1A2F] rounded-lg p-2 text-center text-xs">
        <img src="~/assets/img/ak.png" class="mx-auto mb-1" />
        <p>AK-47</p>
        <p class="text-gray-400">Asimov</p>
      </NuxtLink>
      <NuxtLink to="/product-more" class="bg-[#1D1A2F] rounded-lg p-2 text-center text-xs">
        <img src="~/assets/img/ak.png" class="mx-auto mb-1" />
        <p>AK-47</p>
        <p class="text-gray-400">Asimov</p>
      </NuxtLink>
      <NuxtLink to="/product-more" class="bg-[#1D1A2F] rounded-lg p-2 text-center text-xs">
        <img src="~/assets/img/ak.png" class="mx-auto mb-1" />
        <p>AK-47</p>
        <p class="text-gray-400">Asimov</p>
      </NuxtLink>
    </div>

    <!-- Sold -->
    <h2 class="text-sm text-gray-300 mb-2">Проданы</h2>
    <div class="grid grid-cols-3 gap-3">
      <div class="bg-[#1D1A2F] rounded-lg p-2 text-center text-xs border-b-4 border-red-600">
        <img src="~/assets/img/ak.png" class="mx-auto mb-1" />
        <p>AK-47</p>
        <p class="text-gray-400">Asimov</p>
      </div>
      <div class="bg-[#1D1A2F] rounded-lg p-2 text-center text-xs border-b-4 border-red-600">
        <img src="~/assets/img/ak.png" class="mx-auto mb-1" />
        <p>AK-47</p>
        <p class="text-gray-400">Asimov</p>
      </div>
      <div class="bg-[#1D1A2F] rounded-lg p-2 text-center text-xs border-b-4 border-red-600">
        <img src="~/assets/img/ak.png" class="mx-auto mb-1" />
        <p>AK-47</p>
        <p class="text-gray-400">Asimov</p>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'
import Avatar from '~/assets/img/default-avatar.png'
const user = ref(null)

onMounted(() => {
  const tg = window?.Telegram?.WebApp
  if (tg?.initDataUnsafe?.user) {
    user.value = tg.initDataUnsafe.user
  }
})
</script>

<style scoped>
</style>
