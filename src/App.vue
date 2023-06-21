<template>
  <header class="header">
    <h1 class="header__title">expense tracker</h1>
  </header>
  <section class="section">
    <p class="section__text">Available funds: {{ availableFunds }}</p>
    <p class="section__text--mb">Total expenses: {{ totalExpenses }}</p>
    <hr />
    <p class="section__text--mt">Funds left: {{ fundsLeft }}</p>
  </section>
  <section class="section">
    <h2>Amount</h2>
    <form class="section__form" @submit.prevent="handleFormSubmit">
      <input type="number" placeholder="0" class="section__input" v-model="userAmountInput">
      <button class="section__button">Add Expense</button>
    </form>
  </section>
</template>

<script setup>
import { computed, ref, watch } from 'vue';

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

.section {
  border-radius: 10px;
  box-shadow: rgba(0, 0, 0, 0.35) 0px 5px 15px;
  padding: 16px;
  margin: 40px auto;
  max-width: 600px;
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
