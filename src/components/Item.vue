<template>
  <div class="card my-2 task-list-item">
    <p>{{ task }}</p>
    <div class="btn btn-danger btn-supr" @click="deleteTask">X</div>
  </div>
</template>

<script lang="ts">
import { defineComponent, PropType } from "vue";

export default defineComponent({
  name: "MainContent",
  props: {
    task: {
      type: String,
      require: true,
    },
    deleteTask: {
      type: Function as PropType<(event: MouseEvent) => void>,
      require: true,
    },
  },
  
});
</script>

<style scoped>
.task-list-item {
  position: relative;
  padding: 20px 40px 20px 50px;
  min-height: 80px;
}

.btn-supr {
  position: absolute;
  top: 10px;
  right: 10px;
}

p {
  margin-bottom: 0 !important;
}
</style>
