<template>
    <section class="user-card">
        <h3>{{ user.name }}</h3>
        <BaseButton title="View Projects" @click="emit('selectUser', user)" />
    </section>
</template>

<script setup>
import BaseButton from '../ui/BaseButton.vue';

const props = defineProps({
    user: Object
})

const emit = defineEmits(['selectUser']);
</script>

<style scoped>
.user-card {
    border: 1px solid #ccc;
    box-shadow: rgba(0, 0, 0, 0.16) 0px 3px 6px, rgba(0, 0, 0, 0.23) 0px 3px 6px;
    padding: 16px;
}
</style>