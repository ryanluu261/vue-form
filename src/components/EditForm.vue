<template>
  <div id="popup">
    <button id="XButton" @click="toggleEdit">X</button>
    <form @submit.prevent="updateTodo">
      <label id="label" for="todo">Full name:</label>
      <input type="text" id="form" v-model="name" name="name" placeholder="Your full name..." />

      <label id="label" for="todo">Age:</label>

      <input type="text" id="form" v-model="age" name="age" placeholder="Your age..." />

      <label id="label" for="todo">School:</label>
      <input type="text" id="form" v-model="school" placeholder="Your school..." />

      <input type="submit" id="submitBtn" value="Submit" class="btn" />
    </form>
  </div>
</template>

<script>
export default {
  name: "EditForm",
  
  data() {
    return {
      name: "",
      age: "",
      school: "",
    };
  },
  methods: {
    updateTodo() {
      const newTodo = {
        name: this.name,
        age: this.age,
        school: this.school,
      };

      this.$emit('change-todo', newTodo);

      this.name = this.age = this.school = "";
    },

    toggleEdit() {
      this.$emit('toggle-edit');
    }
  }
};
</script>