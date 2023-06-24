<template>
  <div class="container">
    <ActiveUsers :users="activeUsers" />
    <SelectedUser />
  </div>
</template>

<script setup>
import { provide, ref } from 'vue';

import ActiveUsers from './components/users/ActiveUsers.vue';
import SelectedUser from './components/users/SelectedUser.vue';

const activeUsers = [
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

const selectedUser = ref(null);

provide('selectedUser', selectedUser);
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
