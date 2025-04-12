<template>
  <div class="min-h-screen bg-[#0D0B18] text-white px-4 pt-6 pb-24 relative">
    <!-- Header -->
    <NuxtLink to="/" class="absolute top-4 left-4 text-white text-lg z-10">✕ Назад</NuxtLink>


    <!-- Title -->
    <div class="text-center mb-6">
      <h1 class="text-2xl font-bold">Кейсы</h1>
      <p class="text-sm text-gray-300">Открывай кейсы и получай скины для<br />Counter Strike 2</p>
    </div>

    <!-- Case Grid -->
    <div class="grid grid-cols-2 gap-4 mb-6">
      <div class="bg-[#1D1A2F] p-3 rounded-lg flex flex-col items-center">
        <img src="~/assets/img/gold-box.png" class="w-20 mb-2" />
        <p class="text-sm font-medium mb-1">GOLD Box</p>
        <NuxtLink to="/ruletka" class="border border-white rounded-full px-4 py-1 text-sm">💠 500</NuxtLink>
      </div>

      <div class="bg-[#1D1A2F] p-3 rounded-lg flex flex-col items-center">
        <img src="~/assets/img/blade-box.png" class="w-20 mb-2" />
        <p class="text-sm font-medium mb-1">Blade box</p>
        <NuxtLink to="/ruletka" class="border border-white rounded-full px-4 py-1 text-sm">💠 500</NuxtLink>
      </div>

      <div class="bg-[#1D1A2F] p-3 rounded-lg flex flex-col items-center">
        <img src="~/assets/img/gold-box.png" class="w-20 mb-2" />
        <p class="text-sm font-medium mb-1">GOLD Box</p>
        <NuxtLink to="/ruletka" class="border border-white rounded-full px-4 py-1 text-sm">💠 500</NuxtLink>
      </div>

      <div class="bg-[#1D1A2F] p-3 rounded-lg flex flex-col items-center">
        <img src="~/assets/img/blade-box.png" class="w-20 mb-2" />
        <p class="text-sm font-medium mb-1">Blade box</p>
        <NuxtLink to="/ruletka" class="border border-white rounded-full px-4 py-1 text-sm">💠 500</NuxtLink>
      </div>
    </div>

    <!-- Навигация -->

  </div>
</template>

<script setup>
</script>

<style scoped>
</style>