<template>
    <BaseCard>
        <h2 v-if="!user">No user selected</h2>
        <div v-else>
            <h2 class="selected-user__title">{{ user.name }}: Projects</h2>
            <input type="text" placeholder="Filter items" class="selected-user__input"
                v-model.trim="filteredProjectsInput" />
            <div class="selected-user__projects">
                <UserProject v-for="project in filteredProjects" :key="project.id" :title="project.title" />
            </div>
        </div>
    </BaseCard>
</template>

<script setup>
import { inject, ref, watch } from 'vue';

import BaseCard from '../ui/BaseCard.vue';
import UserProject from './UserProject.vue';

const user = inject('selectedUser');

const filteredProjectsInput = ref('');
const filteredProjects = ref([]);

watch(user, (newValue, _) => {
    filteredProjectsInput.value = '';
    filteredProjects.value = newValue.projects;
});

watch(filteredProjectsInput, () => {
    filteredProjectsInput === '' ? filteredProjects.value = user.value.projects : filteredProjects.value = user.value.projects.filter((project) => project.title.toLowerCase().includes(filteredProjectsInput.value.toLowerCase()))
});

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