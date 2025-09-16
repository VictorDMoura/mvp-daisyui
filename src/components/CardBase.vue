<template>
  <div
    class="card bg-base-100 shadow-sm hover:shadow-md hover:bg-secondary cursor-pointer"
    @click="$emit('clickEpisode')"
  >
    <div class="avatar-group -space-x-6 p-4">
      <div v-for="character in charactersFilter" :key="character.id" class="avatar">
        <div class="w-12">
          <img :src="getImage(character)" :alt="character" />
        </div>
      </div>
      <div v-if="charactersCount > 0" class="avatar avatar-placeholder">
        <div class="bg-neutral text-neutral-content w-12">
          <span>+{{ charactersCount }}</span>
        </div>
      </div>
    </div>
    <div class="card-body">
      <h2 class="card-title">
        {{ name }}
        <BadgeEpisode>{{ episode }}</BadgeEpisode>
      </h2>
      <div class="card-actions justify-end">
        <BadgeAirDate>{{ airDate }}</BadgeAirDate>
      </div>
    </div>
  </div>
</template>

<script setup>
import axios from 'axios'
const emit = defineEmits(['clickEpisode'])

const props = defineProps({
  name: String,
  episode: String,
  airDate: String,
  characters: Array,
})

const charactersFilter = computed(() => {
  if (props.characters.length > 5) {
    const newCharacters = props.characters.slice(0, 5)
    return newCharacters
  }
  return props.characters
})

const charactersCount = computed(() => {
  if (props.characters.length > 5) {
    const count = props.characters.length - 5
    return count
  }
  return 0
})

const getImage = (url) => {
  const id = url.replace('https://rickandmortyapi.com/api/character/', '')
  return `https://rickandmortyapi.com/api/character/avatar/${id}.jpeg`
}
</script>
