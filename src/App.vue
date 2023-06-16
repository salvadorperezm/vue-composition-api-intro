<template>
  <section>
    <h2>Reactive section</h2>
    <h1>{{ user.name }}</h1>
    <h3>{{ user.age }}</h3>
  </section>
  <section>
    <h2>Ref section</h2>
    <p>{{ refValue }}</p>
  </section>
</template>

<script setup>
import { reactive, ref } from 'vue';

const refValue = ref('This was created with ref');

const user = reactive({
  name: 'Salvador',
  age: 23
});

setTimeout(() => {
  user.name = 'Jose';
  user.age = 32;
  refValue.value = 'This was updated using ref';
}, 2000)

</script>

<style scoped></style>
