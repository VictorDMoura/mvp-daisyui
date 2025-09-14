<script setup>
import axios from 'axios'

const episodes = ref([])
const page = ref(1)
const totalPages = ref(0)

const handleGetEspsodios = async () => {
  try {
    const response = await axios.get('https://rickandmortyapi.com/api/episode', {
      params: {
        page: page.value,
      },
    })
    episodes.value = response.data.results
    totalPages.value = response.data.info.pages
  } catch (error) {
    console.error(error)
  }
}

function setPagination(newPage) {
  page.value = newPage
  handleGetEspsodios()
}

onMounted(() => {
  handleGetEspsodios()
})
</script>

<template>
  <div class="p-4">
    <div class="grid grid-cols-1 gap-6 md:grid-cols-2 lg:grid-cols-3">
      <CardBase
        v-for="episode in episodes"
        :key="episode.id"
        :name="episode.name"
        :episode="episode.episode"
        :airDate="episode.air_date"
        :characters="episode.characters"
      />
    </div>
    <div class="flex justify-center py-4">
      <div class="join">
        <button
          v-for="index in totalPages"
          :key="index"
          class="join-item btn btn-lg md:btn-md"
          :class="{ 'btn-active': page === index }"
          @click="setPagination(index)"
        >
          {{ index }}
        </button>
      </div>
    </div>
  </div>
</template>
