<template>
    <BaseCard>
        <h1 class="active-users__title">Active Users</h1>
        <input type="text" placeholder="Filter items" class="active-users__input" />
        <div class="active-users__buttons">
            <BaseButton title="Sort Ascending" />
            <BaseButton title="Sort Descending" />
        </div>
        <div class="active-users__cards">
            <UserCard v-for="user in users" :key="user.id" :user="user" @select-user="selectUser" />
        </div>
    </BaseCard>
</template>

<script setup>
import { inject } from "vue";

import BaseButton from "../ui/BaseButton.vue";
import BaseCard from "../ui/BaseCard.vue";
import UserCard from "./UserCard.vue";

const props = defineProps({
    users: Object
})

const selectedUser = inject('selectedUser');

const selectUser = (user) => {
    selectedUser.value = user;
}
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