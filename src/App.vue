<template>
  <div class="container">
    <ActiveUsers />
    <SelectedUser />
  </div>
</template>

<script setup>
import ActiveUsers from './components/users/ActiveUsers.vue';
import SelectedUser from './components/users/SelectedUser.vue';
</script>

<style scoped>
.container {
  min-height: 100vh;
  min-width: 100vw;
  display: flex;
}

.container>* {
  flex: 1;
}
</style>
