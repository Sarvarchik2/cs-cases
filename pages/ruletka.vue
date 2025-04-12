<template>
  <ClientOnly>
    <div class="min-h-screen bg-[#0D0B18] text-white px-4 pt-6 pb-24 relative overflow-hidden">
      <!-- Header -->
      <NuxtLink to="/" class="absolute top-4 left-4 text-white text-lg z-10">✕ Назад</NuxtLink>

      <!-- Visual Effects -->

      <div class="absolute top-1/2 left-0 w-full h-[3px] bg-gradient-to-r from-transparent via-yellow-500 to-transparent blur-md animate-glow"></div>
      <div class="absolute top-1/2 left-1/2 w-6 h-6 bg-yellow-300 rounded-full opacity-60 blur-xl transform -translate-x-1/2 -translate-y-1/2 animate-ping"></div>

      <!-- Arrows -->
      <div class="absolute  top-[40%] left-0 transform -translate-y-1/2 z-20 w-full flex justify-between px-4 pointer-events-none">
        <div class="text-white text-xl"> > </div>
        <div class="text-white text-xl"> < </div>
      </div>

      <!-- Roulette Scroll View -->
      <div ref="scrollArea" class="mt-20 h-[340px] overflow-y-scroll no-scrollbar relative ruletka-wrapper">
        <div
            v-for="(item, index) in repeatedItems"
            :key="index"
            class="flex flex-col items-center py-4 h-[170px] ruletka"
            :class="{ 'winner-glow': showResult && wonItem.name === item.name && wonItem.desc === item.desc }"
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
      <audio v-for="(track, i) in musicTracks" :key="i" :ref="setAudioRef(i)" :src="track" preload="auto"></audio>
    </div>
  </ClientOnly>
</template>

<script setup>
import { ref, nextTick, onMounted } from 'vue'
import Ak from '@/assets/img/ak.png'
import Awp from "@/assets/img/awp.png"
import Mk from "@/assets/img/mk.png"

const items = [
  { name: 'AK-47', desc: 'Asimov ( Закаленный в боях)', img: Ak },
  { name: 'AWP', desc: 'Gungnir ( Закаленный в боях)', img: Awp },
  { name: 'M4A1', desc: 'Printstream ( Закаленный в боях)', img: Mk }
]

const repeatedItems = Array.from({ length: 80 }, (_, i) => items[i % items.length])
const isSpinning = ref(false)
const scrollArea = ref(null)
const showResult = ref(false)
const wonItem = ref(null)
const audioRef = ref(null)
const musicTracks = [
  '/sounds/music1.mp3', '/sounds/music2.mp3', '/sounds/music3.mp3',
]

const audioTracks = ref([])
function setAudioRef(index) {
  return (el) => {
    if (el) audioTracks.value[index] = el
  }
}

let currentMusic = null
function playRandomMusic() {
  if (currentMusic) {
    currentMusic.pause()
    currentMusic.currentTime = 0
  }
  const track = audioTracks.value[Math.floor(Math.random() * audioTracks.value.length)]
  if (track && typeof track.play === 'function') {
    currentMusic = track
    track.currentTime = 0
    track.volume = 1
    track.play().catch(e => console.error("Audio play error:", e))
  }
}

function stopRandomMusic() {
  if (currentMusic) {
    currentMusic.pause()
    currentMusic.currentTime = 0
    currentMusic = null
  }
}

function animateScrollTo(targetScrollTop, duration = 15000) {
  const startScrollTop = scrollArea.value.scrollTop
  const distance = targetScrollTop - startScrollTop
  let startTime = null

  function animationStep(currentTime) {
    if (!startTime) startTime = currentTime
    const progress = (currentTime - startTime) / duration
    const easeInOut = progress < 0.5
        ? 2 * progress * progress
        : -1 + (4 - 2 * progress) * progress
    const nextScrollTop = startScrollTop + distance * easeInOut
    scrollArea.value.scrollTop = nextScrollTop

    if (progress < 1) {
      requestAnimationFrame(animationStep)
    }
  }

  requestAnimationFrame(animationStep)
}

function spin() {
  isSpinning.value = true
  playRandomMusic()

  const itemHeight = 170
  const visibleCenterOffset = scrollArea.value.clientHeight / 2 - itemHeight / 2
  const targetIndex = Math.floor(Math.random() * (repeatedItems.length - 6)) + 3
  wonItem.value = repeatedItems[targetIndex]

  nextTick(() => {
    const targetScrollTop = targetIndex * itemHeight - visibleCenterOffset
    animateScrollTo(targetScrollTop, 15000)

    setTimeout(() => {
      stopRandomMusic()
      isSpinning.value = false
      showResult.value = true
      audioRef.value?.play()
      localStorage.setItem('lastWin', JSON.stringify(wonItem.value))
    }, 15500)
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
  width: 100%;
}
.ruletka-wrapper {
  height: 68vh;
}
@keyframes glow {
  0%, 100% { opacity: 0.4; }
  50% { opacity: 0.9; }
}
.animate-glow {
  animation: glow 1.6s infinite;
}

@keyframes winnerEffect {
  0% { box-shadow: 0 0 8px 3px rgba(255, 255, 0, 0.7); }
  50% { box-shadow: 0 0 16px 6px rgba(255, 255, 0, 1); }
  100% { box-shadow: 0 0 8px 3px rgba(255, 255, 0, 0.7); }
}
.winner-glow {
  animation: winnerEffect 1.5s infinite ease-in-out;
  border-radius: 8px;
}
</style>
