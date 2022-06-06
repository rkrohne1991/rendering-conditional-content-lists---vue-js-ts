<template>
  <header>
    <h1>Vue Course Goals</h1>
  </header>
  <section id="user-goals">
    <h2>My course goals</h2>
    <input type="text" v-model="enteredGoalValue" />
    <button @click="addGoal">Add Goal</button>
    <p v-if="goals.length === 0">
      No goals have been added yet - please start adding some!
    </p>
    <ul v-else>
      <li
        v-for="(goal, index) in goals"
        :key="index"
        @click="removeGoal(index)"
      >
        <p>{{ goal }} - {{ index }}</p>
        <input type="text" @click.stop />
      </li>
    </ul>
    <!-- <ul>
      <li v-for="num in 10" :key="num">{{ num }}</li>
    </ul> -->
    <!-- <ul>
      <li v-for="(value, key, index) in { name: 'Max', age: 31 }" :key="index">
        {{ key }}: {{ value }}
      </li>
    </ul> -->
  </section>
</template>

<style>
@import './assets/base.css';
</style>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
  data() {
    return { enteredGoalValue: '' as string, goals: [] as Array<string> };
  },
  methods: {
    addGoal() {
      this.goals.push(this.enteredGoalValue);
    },
    removeGoal(idx: number) {
      this.goals.splice(idx, 1);
    },
  },
});
</script>
