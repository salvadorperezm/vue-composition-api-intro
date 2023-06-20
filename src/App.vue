<template>
  <section>
    <h2>Computed properties</h2>
    <h3>{{ displayFullName }}</h3>
    <div>
      <input type="text" placeholder="First name" v-model="firstName">
      <input type="text" placeholder="Last name" v-model="lastName">
    </div>
  </section>
</template>

<script setup>
import { computed, ref } from 'vue';


const firstName = ref('');
const lastName = ref('');

const fullName = computed(() => {
  return `${firstName.value} ${lastName.value}`
})

const displayFullName = computed(() => {
  return !fullName.value.trim() ? "No name input yet" : fullName.value
})
</script>

<style scoped>
.show {
  display: block;
}

.hide {
  display: none;
}
</style>
