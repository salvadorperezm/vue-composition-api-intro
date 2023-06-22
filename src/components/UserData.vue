<template>
    <section>
        <h2>User Data component</h2>
        <p>{{ name }}</p>
        <p>{{ age }}</p>
        <button @click="emit('sayHi', name.toUpperCase())">Say Hi</button>
    </section>
</template>

<script setup>
const props = defineProps({
    name: String,
    age: Number
})

const emit = defineEmits(['sayHi']);
</script>