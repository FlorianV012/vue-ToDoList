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
      <button class="btn btn-primary my-3" @click.prevent="createNewTask">
        Create task
      </button>
    </form>

    <ul>
      <li v-for="(task, index) in tasksArray" :key="index">
        <item :id="index" :task="task" :deleteTask="deleteTask" />
      </li>
    </ul>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import Item from "./Item.vue";

interface IFormData {
  task: string;
}

export default defineComponent({
  name: "MainContent",
  components: {
    item: Item,
  },
  data() {
    return {
      formData: {
        task: "",
      } as IFormData,
      tasksArray: ["task 1", "task 2", "task 3"] as string[],
    };
  },
  methods: {
    createNewTask(this: { formData: IFormData; tasksArray: string[] }) {
      if (this.formData.task.trim() !== "") {
        this.tasksArray.push(this.formData.task);
        this.formData.task = "";
      }
    },
    deleteTask(this: { tasksArray: string[] }, e: MouseEvent) {
      const target = e.target as HTMLElement;
      const parentNode = target.parentNode;

      if (parentNode instanceof HTMLElement) {
        const taskId = parentNode.id;

        this.tasksArray.splice(parseInt(taskId), 1);
      }
    },
  },
});
</script>

<style>
ul {
  list-style-type: none;
  padding: 0 !important;
}
</style>
