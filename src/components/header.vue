<template>
  <header>
    <h1>{{ title }}</h1>
    <ButtonComponent
      @btn-click="$emit('toggle-add-task')"
      :text="showAddTask ? 'Close' : 'AddTask'"
      :color="showAddTask ? 'red' : 'green'"
    />
  </header>
</template>

<script>
import ButtonComponent from "./Button";

export default {
  name: "HeaderComponent",
  props: {
    title: String,
    showAddTask: Boolean,
  },
  components: { ButtonComponent },
};
</script>
<style scooped>
header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 20px;
}
</style>
