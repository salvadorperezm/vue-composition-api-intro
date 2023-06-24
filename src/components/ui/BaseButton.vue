<template>
    <button class="button">{{ title }}</button>
</template>

<script setup>
const props = defineProps({
    title: String
})
</script>

<style scoped>
.button {
    border: 1px solid #232671;
    background-color: #ffffff;
    color: #232671;
    cursor: pointer;
    font-size: 16px;
    padding: 10px 20px;
}

.button:hover {
    background-color: #eeedff;
}

.button--active {
    background-color: #232671;
    border: 1px solid transparent;
    color: #ffffff;
    font-size: 16px;
    padding: 10px 20px;
}
</style>