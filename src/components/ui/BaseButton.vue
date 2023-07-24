<template>
    <button class="button" :class="{ active: type === currentSortingMethod }" @click="$emit('toggleSort', type)">{{ title
    }}</button>
</template>

<script setup>
const props = defineProps({
    title: String,
    type: String,
    currentSortingMethod: String
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

.active {
    background-color: #232671;
    border: 1px solid transparent;
    color: #ffffff;
    font-size: 16px;
    padding: 10px 20px;
}
</style>