<template>
  <div :key="task.id" v-for="task in tasks">
    <h3>{{ task.text }}</h3>
    <TaskComponent
      @toggle-reminder="$emit('toggle-reminder', task.id)"
      @delete-task="$emit('delete-task', task.id)"
      :task="task"
    />
  </div>
</template>

<script>
import TaskComponent from "./Task"; // Assuming TaskComponent is in the same directory

export default {
  name: "TasksComponent",
  props: {
    tasks: Array,
  },
  components: {
    TaskComponent,
  },
  emits: ["delete-task", "toggle-reminder"],
};
</script>
