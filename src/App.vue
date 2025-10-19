<script setup lang="ts">
import { ref } from 'vue'
import sample_cards from './data/samplecards.json'

const view_button_text = ref('Show Answer')
const current_side = ref('question')

const current_index = ref(0)
const cards = ref(sample_cards)

const prevCard = () => {
  if (current_index.value > 0) {
    current_index.value--
  }
}

const nextCard = () => {
  if (current_index.value < cards.value.length - 1) {
    current_index.value++
  }
}

const handleView = () => {
  if (current_side.value == 'question') {
    current_side.value = 'answer'
    view_button_text.value = 'Hide Answer'
  } else {
    current_side.value = 'question'
    view_button_text.value = 'Show Answer'
  }
}
</script>

<template>
  <!-- HACK: Temporarily made the screen sort of centered vertically -->
  <div class="h-screen flex items-center justify-center">
    <div class="flex flex-col w-full gap-5 max-w-5xl mx-auto items-center mb-15">
      <div class="flex flex-row w-full">
        <h1 class="text-5xl font-bold flex">Splash</h1>
        <div class="text-lg flex items-center justify-end w-full">
          <h6>{{ current_index + 1 }}/{{ cards.length }}</h6>
        </div>
      </div>

      <progress class="progress w-full" :value="current_index + 1" :max="cards.length"></progress>

      <div class="card bg-base-300 shadow-lg w-full">
        <div class="card-body">
          <div v-if="cards.length">
            <div class="h-50 flex justify-center items-center">
              <p v-if="current_side == 'question'" class="text-3xl text-center w-full">
                {{ cards[current_index]?.question }}
              </p>
              <p v-else-if="current_side == 'answer'" class="text-3xl text-center w-full">
                {{ cards[current_index]?.answer }}
              </p>
            </div>
          </div>

          <div class="bg-base-600 flex flex-row w-full">
            <div class="w-1/3 flex justify-start">
              <button class="btn font-light" @click="prevCard">Previous</button>
            </div>
            <div class="w-1/3 flex justify-center">
              <button class="btn" @click="handleView">
                {{ view_button_text }}
              </button>
            </div>
            <div class="w-1/3 flex justify-end">
              <button class="btn" @click="nextCard">Next</button>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped></style>
