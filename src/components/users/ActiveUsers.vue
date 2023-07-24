<template>
    <BaseCard>
        <h1 class="active-users__title">Active Users</h1>
        <input type="text" placeholder="Filter items" class="active-users__input" v-model.trim="filteredUsersInput" />
        <div class="active-users__buttons">
            <BaseButton title="Sort Ascending" type="asc" :currentSortingMethod="currentSortingMethod"
                @toggle-sort="toggleSorting" />
            <BaseButton title="Sort Descending" type="desc" :currentSortingMethod="currentSortingMethod"
                @toggle-sort="toggleSorting" />
        </div>
        <div class="active-users__cards">
            <UserCard v-for="user in filteredUsers" :key="user.id" :user="user" @select-user="selectUser" />
        </div>
    </BaseCard>
</template>

<script setup>
import { inject, ref, watch } from "vue";

import BaseButton from "../ui/BaseButton.vue";
import BaseCard from "../ui/BaseCard.vue";
import UserCard from "./UserCard.vue";

const users = [
    {
        id: 'users-4',
        name: 'John Doe',
        projects: [
            {
                id: 'projects-10',
                title: 'Write product documentation'
            },
            {
                id: 'projects-11',
                title: 'Test software application'
            },
            {
                id: 'projects-12',
                title: 'Troubleshoot user issues'
            }
        ]
    },
    {
        id: 'users-2',
        name: 'Manuel Lorenz',
        projects: [
            {
                id: 'projects-4',
                title: 'Develop website layout'
            },
            {
                id: 'projects-5',
                title: 'Implement user authentication'
            },
            {
                id: 'projects-6',
                title: 'Optimize database queries'
            }
        ]
    },
    {
        id: 'users-3',
        name: 'Jane Smith',
        projects: [
            {
                id: 'projects-7',
                title: 'Design marketing campaign'
            },
            {
                id: 'projects-8',
                title: 'Create social media content'
            },
            {
                id: 'projects-9',
                title: 'Analyze customer data'
            }
        ]
    }
]

const selectedUser = inject('selectedUser');

const selectUser = (user) => {
    selectedUser.value = user;
}

const filteredUsersInput = ref('');
const filteredUsers = ref(users);

watch(filteredUsersInput, () => {
    filteredUsersInput === '' ? filteredUsers.value = users : filteredUsers.value = users.filter((user) => user.name.toLowerCase().includes(filteredUsersInput.value.toLowerCase()))
})

const currentSortingMethod = ref('asc');

const toggleSorting = (value) => {
    currentSortingMethod.value = value;
}

watch([filteredUsers, currentSortingMethod], () => {
    currentSortingMethod.value === 'asc' ? filteredUsers.value.sort((a, b) => a.name > b.name ? 1 : -1) : filteredUsers.value.sort((a, b) => a.name < b.name ? 1 : -1);
});
</script>

<style scoped>
.active-users__title {
    margin-block-end: 30px;
    font-size: 28px;
}

.active-users__input {
    width: 100%;
    border: 1px solid #ccc;
    padding: 8px 4px;
    font-size: 16px;
}

.active-users__buttons {
    align-items: center;
    display: flex;
    gap: 10px;
    margin-block-start: 10px;
}

.active-users__cards {
    display: flex;
    flex-direction: column;
    gap: 20px;
    margin-block-start: 20px;
}
</style>