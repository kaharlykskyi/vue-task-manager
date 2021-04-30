<template>
  <form @submit.prevent="onSubmit" class="add-form">
    <div class="form-control">
      <label>Name</label>
      <input type="text" v-model="text" name="text" placeholder="Name" />
    </div>
    <div class="form-control">
      <label>Day & Time</label>
      <input
          type="text"
          v-model="day"
          name="day"
          placeholder="Day & Time"
      />
    </div>
    <div class="form-control form-control-check">
      <label>Set reminder</label>
      <input type="checkbox" v-model="reminder" name="reminder" />
    </div>

    <input type="submit" value="Save Task" class="btn btn-block" />
  </form>
</template>

<script>
export default {
  name: "AddTask",
  data() {
    return {
      text: '',
      day: '',
      reminder: false
    }
  },
  methods: {
    onSubmit(e) {
      if(!this.text) {
        alert('Please add a task')
        return
      }

      const newTask = {
        text: this.text,
        day: this.day,
        reminder: this.reminder
      }

      this.$emit('add-task', newTask);

      this.text = ''
      this.day = ''
      this.reminder = false
    }
  }
}
</script>

<style scoped>
  .add-form {
    margin-bottom: 40px;
  }
  .form-control {
    margin: 20px 0;
  }
  .form-control label {
    display: block;
  }
  .form-control input {
    width: 100%;
    height: 40px;
    margin: 5px;
    padding: 3px 7px;
    font-size: 14px;
    border-radius: 5px;
    border: 1px solid #ccc;
  }
  .form-control-check {
    display: flex;
    align-items: center;
    justify-content: space-between;
  }
  .form-control-check label {
    flex: 1;
  }
  .form-control-check input {
    flex: 2;
    height: 20px;
  }
</style>