<template>
  <div class="container">
    <HeaderComponent
      @toggle-add-task="toggleAddTask"
      title="Task Tracker"
      :showAddTask="showAddTask"
    />
    <div v-show="showAddTask">
      <AddTask @add-task="addTask" />
    </div>
    <TasksComponent
      @toggle-reminder="toggleReminder"
      @delete-task="deleteTask"
      :tasks="tasks"
    />
  </div>
</template>

<script>
import HeaderComponent from "./components/header";
import TasksComponent from "./components/Tasks";
import AddTask from "./components/AddTask";

export default {
  name: "App",
  components: {
    HeaderComponent,
    TasksComponent,
    AddTask,
  },
  data() {
    return {
      tasks: [],
      showAddTask: false,
    };
  },
  methods: {
    toggleAddTask() {
      this.showAddTask = !this.showAddTask;
    },
    addTask(task) {
      this.tasks = [...this.tasks, task];
    },
    deleteTask(id) {
      if (confirm("Are you sure?"))
        this.tasks = this.tasks.filter((task) => task.id !== id);
    },
    toggleReminder(id) {
      this.tasks = this.tasks.map((task) =>
        task.id === id ? { ...task, reminder: !task.reminder } : task
      );
    },
  },

  created() {
    this.tasks = [
      {
        id: 1,
        text: "Doctor appointment",
        day: "Sept 1st at 2:00pm",
        reminder: true,
      },
      {
        id: 2,
        text: "Hair Appointement",
        day: "Sept 7th at 8:00am",
        reminder: true,
      },
      {
        id: 3,
        text: "Shopping",
        day: "Sept 11th at 11:00am",
        reminder: false,
      },
    ];
  },
};
</script>
