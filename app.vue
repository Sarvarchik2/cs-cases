<template>
  <div>
    <NuxtRouteAnnouncer />
    <NuxtPage />
    <div class="fixed bottom-0 left-0 right-0 bg-[#1D1A2F] text-white flex justify-around py-2 border-t border-gray-800">
      <NuxtLink to="/" class="flex flex-col items-center text-yellow-400 font-bold">U<br /><span class="text-xs">777</span></NuxtLink>
      <NuxtLink to="/shop" class="flex flex-col items-center text-gray-300">🏪<br /><span class="text-xs">Магазин</span></NuxtLink>
      <NuxtLink to="/friends" class="flex flex-col items-center text-gray-300">👥<br /><span class="text-xs">Друзья</span></NuxtLink>
      <NuxtLink to="/profile" class="flex flex-col items-center text-gray-300">👤<br /><span class="text-xs">Профиль</span></NuxtLink>
    </div>

    <!-- Footer -->
    <p class="text-xs text-gray-500 mt-6">Powered by “U Holding”</p>
  </div>
</template>


<script setup>
useHead({
  meta: [
    {
      name: 'viewport',
      content: 'width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no'
    }
  ]
})
</script>
