<template>
    <div class="user-project__container">
        <h4 class="user-project__title">{{ title }}</h4>
    </div>
</template>

<script setup>
const props = defineProps({
    title: String
})
</script>

<style scoped>
.user-project__container {
    background-color: #000564;
    color: #ffffff;
    padding: 8px;
}
</style>