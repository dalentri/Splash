<script setup lang="ts">
import { ref } from 'vue'

// TODO: Make a it so where the card can flip
const question_side = ref('')
const answer_side = ref('')
const view_button_text = ref('Show Answer')

//TODO: Make handling of which side the card is on
const current_side = ref('question')

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
  <div class="flex flex-col m-70 gap-5">
    <div class="flex flex-row">
      <h1 class="text-5xl font-bold flex">Splash</h1>
      <div class="text-lg flex items-center justify-end w-full"><h6>5/20</h6></div>
    </div>

    <progress class="progress" value="40" max="100"></progress>
    <div class="card bg-base-300 shadow-lg">
      <div class="card-body">
        <div class="h-50 flex">
          <p v-if="current_side == 'question'" class="text-3xl flex justify-center items-center">
            Sample Text of the front side of the card
          </p>
          <p v-else-if="current_side == 'answer'" class="text-lg flex justify-center items-center">
            Answer side of the flash card
          </p>
        </div>
        <div class="bg-base-600 flex flex-row w-full">
          <div class="w-1/3 flex justify-start">
            <button class="btn font-light">< Previous</button>
          </div>

          <div class="w-1/3 flex justify-center">
            <button class="btn" @click="handleView">
              {{ view_button_text }}
            </button>
          </div>

          <div class="w-1/3 flex justify-end">
            <button class="btn justify-end">Next ></button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped></style>
