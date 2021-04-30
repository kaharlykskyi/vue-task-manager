<template>
  <div @dblclick="$emit('toggle-reminder', task.id)" :class="[task.reminder ? 'reminder' : '', 'task']">
    <h3>{{ task.text }}
      <i @click="$emit('delete-task', task.id)" class="fas fa-times"></i>
    </h3>
    <p>{{ task.day }}</p>
  </div>
</template>

<script>
export default {
  name: "Task",
  props: {
    task: Object
  }
}
</script>

<style scope>
  .fas {
    color: #dc0000;
  }
  .task {
    cursor: pointer;
    border-radius: 4px;
    background: #f4f4f4;
    margin: 5px;
    padding: 10px 20px;
  }
  .task.reminder {
    border-left: 7px solid #03af03;
  }
  .task h3 {
    display: flex;
    align-items: center;
    justify-content: space-between;
  }
  .task p {
    font-weight: 100;
  }
</style>