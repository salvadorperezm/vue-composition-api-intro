<template>
  <section>
    <h2>My course goal</h2>
    <!-- Task 1: Output your main course goal with the help of the composition API -->
    <!-- Don't hardcode it into the template, instead hardcode it into the JS code -->
    <h3 :class="goalVisibility">{{ courseGoal }}</h3>
    <!-- Task 2: Toggle (show/hide) the goal with the help of the button -->
    <button @click="toggleGoal">Toggle Goal</button>
    <!-- Task 3: manage data in three ways -->
    <!-- => Separate refs -->
    <!-- => Ref object -->
    <!-- => Reactive object -->
    <!-- Task 4: Also solve the assignment with the Options API -->
  </section>
  <hr />
  <section>
    <h2>My course goal</h2>
    <!-- Task 1: Output your main course goal with the help of the composition API -->
    <!-- Don't hardcode it into the template, instead hardcode it into the JS code -->
    <h3 :class="refObject.refGoalVisibility">{{ refObject.refCourseGoal }}</h3>
    <!-- Task 2: Toggle (show/hide) the goal with the help of the button -->
    <button @click="refToggleGoal">Toggle Goal</button>
    <!-- Task 3: manage data in three ways -->
    <!-- => Separate refs -->
    <!-- => Ref object -->
    <!-- => Reactive object -->
    <!-- Task 4: Also solve the assignment with the Options API -->
  </section>
  <hr>
  <section>
    <h2>My course goal</h2>
    <!-- Task 1: Output your main course goal with the help of the composition API -->
    <!-- Don't hardcode it into the template, instead hardcode it into the JS code -->
    <h3 :class="reactiveObject.reactiveGoalVisibility">{{ reactiveObject.reactiveCourseGoal }}</h3>
    <!-- Task 2: Toggle (show/hide) the goal with the help of the button -->
    <button @click="reactiveToggleGoal">Toggle Goal</button>
    <!-- Task 3: manage data in three ways -->
    <!-- => Separate refs -->
    <!-- => Ref object -->
    <!-- => Reactive object -->
    <!-- Task 4: Also solve the assignment with the Options API -->
  </section>
</template>

<script setup>
import { reactive, ref } from 'vue';

// Separate refs
const courseGoal = ref('My goal is to lear as much as I can from Vue and to start using it in real projects.');
const goalVisibility = ref('show');

const toggleGoal = () => {
  if (goalVisibility.value === 'show') {
    goalVisibility.value = 'hide'
  } else {
    goalVisibility.value = 'show'
  }
}

// Ref object
const refObject = ref({
  refCourseGoal: 'My goal is to lear as much as I can from Vue and to start using it in real projects.',
  refGoalVisibility: 'show'
})

const refToggleGoal = () => {
  if (refObject.value.refGoalVisibility === 'show') {
    refObject.value.refGoalVisibility = 'hide'
  } else {
    refObject.value.refGoalVisibility = 'show'
  }
}

// Reactive
const reactiveObject = reactive({
  reactiveCourseGoal: 'My goal is to lear as much as I can from Vue and to start using it in real projects.',
  reactiveGoalVisibility: 'show'
})

const reactiveToggleGoal = () => {
  if (reactiveObject.reactiveGoalVisibility === 'show') {
    reactiveObject.reactiveGoalVisibility = 'hide'
  } else {
    reactiveObject.reactiveGoalVisibility = 'show'
  }
}
</script>

<style scoped>
.show {
  display: block;
}

.hide {
  display: none;
}
</style>
