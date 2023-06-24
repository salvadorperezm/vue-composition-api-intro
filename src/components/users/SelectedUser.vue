<template>
    <BaseCard>
        <h2 v-if="!user">No user selected</h2>
        <div v-else>
            <h2 class="selected-user__title">{{ user.name }}: Projects</h2>
            <input type="text" placeholder="Filter items" class="selected-user__input" />
            <div class="selected-user__projects">
                <UserProject v-for="project in user.projects" :key="project.id" :title="project.title" />
            </div>
        </div>
    </BaseCard>
</template>

<script setup>
import { inject } from 'vue';

import BaseCard from '../ui/BaseCard.vue';
import UserProject from './UserProject.vue';

const user = inject('selectedUser');
</script>

<style scoped>
.selected-user__title {
    margin-block-end: 30px;
}

.selected-user__projects {
    display: flex;
    flex-direction: column;
    gap: 10px;
    margin-block-start: 20px;
}

.selected-user__input {
    width: 100%;
    border: 1px solid #ccc;
    padding: 8px 4px;
    font-size: 16px;
}
</style>