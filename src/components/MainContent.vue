<template>
  <div class="container">
    <h1>TODO List</h1>

    <form>
      <div class="form-group">
        <label for="newTask">Create new task</label>
        <input
          class="form-control"
          type="text"
          id="newTask"
          v-model="formData.task"
        />
      </div>
      <button class="btn btn-primary my-3">Create task</button>
    </form>

    <ul>
      <li v-for="(task, index) in tasksArray" :key="index">
        <item :id="index" :task="task" />
      </li>
    </ul>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import Item from "./Item.vue";

export default defineComponent({
  name: "MainContent",
  components: {
    item: Item,
  },
  data() {
    return {
      formData: {
        task: "",
      },
      tasksArray: ["task 1", "task 2", "task 3"],
    };
  },
  methods: {},
});
</script>

<style>
ul {
  list-style-type: none;
  padding: 0!important;
}
</style>
