<template>
  <div class="min-h-screen bg-[#0D0B18] text-white px-4 pt-6 pb-24 relative overflow-hidden">
    <!-- Header -->
    <NuxtLink to="/" class="absolute top-4 left-4 text-white text-lg z-10">✕ Назад</NuxtLink>

    <!-- Indicator Arrows -->
    <!-- Indicator Arrows -->
    <div class="absolute top-[42%] left-0 transform -translate-y-1/2 z-20 w-full flex justify-between px-4 pointer-events-none">
      <div class="text-white text-xl"> > </div>
      <div class="text-white text-xl"> < </div>
    </div>


    <!-- Roulette Scroll View -->
    <div ref="scrollArea" class="mt-20 h-[340px] overflow-y-scroll no-scrollbar relative ruletka-wrapper">
      <div
          v-for="(item, index) in repeatedItems"
          :key="index"
          class="flex flex-col items-center py-4 h-[170px] ruletka"
      >
        <img :src="item.img" class="w-40 mb-1" />
        <p class="text-md font-semibold">{{ item.name }}</p>
        <p class="text-xs text-gray-400">{{ item.desc }}</p>
      </div>
    </div>

    <!-- Button -->
    <button @click="spin" :disabled="isSpinning" class="w-full mt-12 bg-[#F7D774] text-black py-3 rounded-lg font-semibold flex justify-center items-center gap-2 disabled:opacity-50">
      <span v-if="!isSpinning">Открыть <span class="text-sm">💠 500</span></span>
      <span v-else>Открытие...</span>
    </button>

    <!-- Result Modal -->
    <div v-if="showResult" class="fixed inset-0 bg-black bg-opacity-70 flex items-center justify-center z-50">
      <div class="bg-[#1D1A2F] p-6 rounded-xl text-center w-80 animate-pulse">
        <img :src="wonItem.img" class="w-32 mx-auto mb-4" />
        <h2 class="text-lg font-bold mb-1">{{ wonItem.name }}</h2>
        <p class="text-sm text-gray-400 mb-4">{{ wonItem.desc }}</p>
        <div class="flex justify-between mb-4">
          <button class="bg-red-600 text-white px-4 py-2 rounded-lg text-sm">Продать за 100 💠</button>
          <button class="bg-gray-700 text-white px-4 py-2 rounded-lg text-sm">Поделиться</button>
        </div>
        <button @click="closeModal" class="bg-[#F7D774] text-black w-full py-2 rounded-lg font-semibold">Оставить</button>
      </div>
    </div>
    <audio ref="audioRef" src="/sounds/win.mp3" preload="auto"></audio>
  </div>
</template>

<script setup>
import { ref, nextTick } from 'vue'
import Ak from '@/assets/img/ak.png'
import Awp from "@/assets/img/awp.png"
import Mk from "@/assets/img/mk.png"

const items = [
  { name: 'AK-47', desc: 'Asimov ( Закаленный в боях)', img: Ak },
  { name: 'AWP', desc: 'Gungnir ( Закаленный в боях)', img: Awp },
  { name: 'M4A1', desc: 'Printstream ( Закаленный в боях)', img: Mk }
]

const repeatedItems = Array.from({ length: 50 }, (_, i) => items[i % items.length])
const isSpinning = ref(false)
const scrollArea = ref(null)
const showResult = ref(false)
const wonItem = ref(null)
const audioRef = ref(null)

function spin() {
  isSpinning.value = true
  const itemHeight = 170
  const padding = 85
  const visibleCenterOffset = scrollArea.value.clientHeight / 2 - itemHeight / 2
  const targetIndex = Math.floor(Math.random() * (repeatedItems.length - 6)) + 3
  wonItem.value = repeatedItems[targetIndex]

  nextTick(() => {
    scrollArea.value.scrollTo({
      top: targetIndex * itemHeight - visibleCenterOffset,
      behavior: 'smooth'
    })
    setTimeout(() => {
      isSpinning.value = false
      showResult.value = true
      audioRef.value?.play()
      localStorage.setItem('lastWin', JSON.stringify(wonItem.value))
    }, 3000)
  })
}

function closeModal() {
  showResult.value = false
}
</script>

<style scoped>
.no-scrollbar::-webkit-scrollbar {
  display: none;
}
.no-scrollbar {
  -ms-overflow-style: none;
  scrollbar-width: none;
}
.ruletka img {
  width: 77%;
}
.ruletka-wrapper {
  height: 68vh;
}
</style>
