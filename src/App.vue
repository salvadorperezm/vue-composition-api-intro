<template>
  <header class="header">
    <h1 class="header__title">expense tracker</h1>
  </header>
  <section class="section">
    <p class="section__text">Available funds: 200</p>
    <p class="section__text--mb">Total expenses: 0</p>
    <hr />
    <p class="section__text--mt">Funds left: 100</p>
  </section>
  <section class="section">
    <h2>Amount</h2>
    <input type="number" placeholder="0" class="section__input">
    <button class="section__button">Add Expense</button>
  </section>
</template>

<script setup>
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
