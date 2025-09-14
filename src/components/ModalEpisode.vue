<template>
  <dialog id="modal-episode" class="modal" :class="{ 'modal-open': show }">
    <div v-if="episode" class="modal-box">
      <form method="dialog">
        <button class="btn btn-sm btn-circle btn-ghost absolute right-2 top-2" @click="handleClose">
          ✕
        </button>
      </form>
      <h3 class="text-lg font-bold mb-4">
        {{ episode.name }}
        <BadgeEpisode>{{ episode.episode }}</BadgeEpisode>
      </h3>
      <div v-for="character in episode.characters" :key="character" class="avatar">
        <div class="w-12 rounded-full">
          <img :src="getImage(character)" />
        </div>
      </div>
      <p class="py-4">
        <BadgeAirDate>{{ episode.air_date }}</BadgeAirDate>
      </p>
      <p class="py-4">Press ESC key or click on ✕ button to close</p>
    </div>
    <div v-else class="modal-box">
      <div class="flex justify-center">
        <span class="loading loading-ring loading-lg"></span>
      </div>
    </div>
  </dialog>
</template>

<script setup>
import axios from 'axios'
const props = defineProps({
  id: Number,
})
const episode = ref({})
const show = defineModel()

const handleGetEspisode = async () => {
  try {
    const response = await axios.get(`https://rickandmortyapi.com/api/episode/${props.id}`)
    episode.value = response.data
  } catch (error) {
    console.error(error)
  }
}

const getImage = (url) => {
  const id = url.replace('https://rickandmortyapi.com/api/character/', '')
  return `https://rickandmortyapi.com/api/character/avatar/${id}.jpeg`
}

function handleClose() {
  show.value = false
}

watch(show, (newValue) => {
  if (newValue) {
    handleGetEspisode()
  } else {
    episode.value = {}
  }
})
</script>
