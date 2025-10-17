<script setup lang="ts">
import { ref } from 'vue'

// TODO: Make a it so where the card can flip
let question_side = ref('')
let answer_side = ref('')

//TODO: Make handling of which side the card is on
const current_side = ref('question')

const handleView = () => {
  if (current_side.value == 'question') {
    current_side.value = 'answer'
  } else {
    current_side.value = 'question'
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
        <div class="h-50">
          <h1 v-if="current_side == 'question'" class="flex justify-center">
            Sample Text of the front side of the card
          </h1>
          <p v-else-if="current_side == 'answer'" class="flex justify-center">
            Answer side of the flash card
          </p>
        </div>
        <div class="bg-base-600 flex flex-row">
          <button class="btn font-light">< Previous</button>
          <div class="flex justify-end w-full"><button class="btn justify-end">Next ></button></div>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped></style>
