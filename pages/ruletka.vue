

<template>
  <div class="min-h-screen bg-[#0D0B18] text-white px-4 pt-6 pb-24 relative overflow-hidden">
    <!-- Header -->
    <NuxtLink to="/" class="absolute top-4 left-4 text-white text-lg z-10">✕ Назад</NuxtLink>

    <!-- Roulette Frame -->
    <div class="relative w-full max-w-sm mx-auto mt-20 h-52 overflow-hidden border-y-4 border-yellow-400 z-0">
      <div
          ref="reel"
          class="flex flex-col items-center transition-transform duration-1000 ease-out"
          :style="{ transform: `translateY(-${translateY}px)` }"
      >
        <div
            v-for="(item, index) in repeatedItems"
            :key="index"
            class="flex flex-col items-center py-4"
        >
          <img :src="item.img" class="w-32 mb-1" />
          <p class="text-md font-semibold">{{ item.name }}</p>
          <p class="text-xs text-gray-400">{{ item.desc }}</p>
        </div>
      </div>
    </div>

    <!-- Button -->
    <button @click="spin" class="w-full mt-12 bg-[#F7D774] text-black py-3 rounded-lg font-semibold flex justify-center items-center gap-2">
      Открыть <span class="text-sm">💠 500</span>
    </button>
  </div>
</template>

<script setup>
import { ref } from 'vue'

import Ak from '@/assets/img/ak.png'
import Awp from "@/assets/img/awp.png"
import Mk from "@/assets/img/mk.png"

const items = [
  { name: 'AK-47', desc: 'Asimov ( Закаленный в боях)', img: Ak },
  { name: 'AK-47', desc: 'Asimov ( Закаленный в боях)', img: Ak },
  { name: 'AK-47', desc: 'Asimov ( Закаленный в боях)', img: Ak },
  { name: 'AK-47', desc: 'Asimov ( Закаленный в боях)', img: Ak },
  { name: 'AK-47', desc: 'Asimov ( Закаленный в боях)', img: Ak },
  { name: 'AWP', desc: 'Gungnir ( Закаленный в боях)', img: Awp },
  { name: 'M4A1', desc: 'Printstream ( Закаленный в боях)', img: Mk }
]

const repeatedItems = Array.from({ length: 20 }, (_, i) => items[i % items.length])
const itemHeight = 180
const translateY = ref(0)

function spin() {
  const totalItems = repeatedItems.length
  const targetIndex = Math.floor(Math.random() * totalItems)
  translateY.value = targetIndex * itemHeight
}
</script>

<style scoped>
</style>