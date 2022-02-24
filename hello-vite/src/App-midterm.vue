<script setup>
import { ref } from "vue";

// generates random number in range (1-99)
const generateNumber = () => {
  let duplicate = false;
  const rand = Math.floor(Math.random() * 99 + 1);
  duplicate = randNumbers.value.some((randNumber) => randNumber === rand);
  duplicate ? generateNumber() : randNumbers.value.push(rand);
};

const student = ["63130500055", "Tarathep Siripis"];

const randNumbers = ref([]);
const generate = () => {
  generateNumber();
  console.log(randNumbers.value);
};
</script>

<template>
  <div class="top-container">
    <div class="action-button">
      <button @click="generate">Generate New Number</button>
      <button>Reset</button>
    </div>
    <p v-for="(me, index) in student" :key="index">{{ me }}</p>
    <div class="error-message">
      <!-- show error message when a user adding the same number in the bingo sheet -->
    </div>
    <div class="grid-container">
      <div v-for="index in 9" :key="index" class="grid-item">
        <!-- show bingo 3 rows x 3 cols here -->
        <a v-if="randNumbers.length === 0">
          <button class="butt" :disabled="!isActive" @click.prevent>AddNumber</button>
        </a>
        <a v-else>
          <button class="butt" :disabled="isActive" @click.prevent>AddNumber</button>
        </a>
      </div>
    </div>
    <div class="generate-number">
      <!-- show the list of generated number here -->
      <li
        v-for="(numb, index) in randNumbers"
        :key="index"
      >Generate Number #{{ index + 1 }} : ' {{ numb }} '</li>
    </div>
  </div>
</template>

<style scoped>
.top-container {
  width: 330px;
}
.action-button {
  padding: 10px;
  display: flex;
  gap: 5px;
}
.grid-container {
  display: grid;
  grid-template-columns: 100px 100px 100px;
  grid-template-rows: 80px 80px 80px;
  column-gap: 5px;
  row-gap: 5px;
  background-color: green;
  padding: 10px;
}
.grid-item {
  display: flex;
  background-color: rgba(255, 255, 255, 0.8);
  border: 1px solid rgba(0, 0, 0, 0.8);
  font-size: 30px;
  text-align: center;
  justify-content: center;
  align-items: center;
  cursor: pointer;
}
.generate-number {
  font-size: 20px;
}
.error-message {
  height: 40px;
  color: red;
}
</style>
