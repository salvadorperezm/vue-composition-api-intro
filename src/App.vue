<template>
  <header class="header">
    <h1 class="header__title">expense tracker</h1>
  </header>
  <BaseCard>
    <p class="section__text">Available funds: {{ availableFunds }}</p>
    <p class="section__text--mb">Total expenses: {{ totalExpenses }}</p>
    <hr />
    <p class="section__text--mt">Funds left: {{ fundsLeft }}</p>
  </BaseCard>
  <BaseCard>
    <h2>Amount</h2>
    <form class="section__form" @submit.prevent="handleFormSubmit">
      <input type="number" placeholder="0" class="section__input" v-model="userAmountInput">
      <button class="section__button">Add Expense</button>
    </form>
  </BaseCard>
  <BaseCard>
    <UserData name="Salvador Perez" :age="23" @say-hi="sayHi" />
  </BaseCard>
</template>

<script setup>
import { computed, ref, watch } from 'vue';

import BaseCard from "./components/BaseCard.vue"
import UserData from './components/UserData.vue';

const availableFunds = ref(100);
const totalExpenses = ref(0);
const userAmountInput = ref(0);

const handleFormSubmit = () => {
  totalExpenses.value += userAmountInput.value;
  userAmountInput.value = 0;
}

const fundsLeft = computed(() => {
  return availableFunds.value - totalExpenses.value;
})

watch(fundsLeft, () => {
  fundsLeft.value < 0 && alert('You are broke!');
})

const sayHi = (name) => {
  alert(`Hello world, I am ${name}`);
}
</script>

<style scoped>
.header {
  background-color: #2c0966;
  color: #ffffff;
  padding: 32px;
  text-align: center;
}

.header__title {
  font-size: 48px;
  text-transform: capitalize;
}

.section__button {
  background-color: #2c0966;
  border: none;
  color: #ffffff;
  cursor: pointer;
  display: block;
  font-size: 16px;
  margin-block-start: 10px;
  padding: 8px 16px;
}

.section__input {
  width: 100%;
}

.section__text,
.section__text--mb,
.section__text--mt {
  font-size: 18px;
}

.section__text--mb {
  margin-block-end: 10px;
}

.section__text--mt {
  margin-block-start: 10px;
}
</style>
