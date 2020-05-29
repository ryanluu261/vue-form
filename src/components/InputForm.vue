<template>
  <div id="popup">
    <button id="XButton" @click="toggleForm">X</button>
    <form @submit.prevent="addTodo">
      <label id="label" for="todo">Full name:</label>
      <input type="text" id="form" v-model="name" name="name" placeholder="Your full name..." />

      <label id="label" for="todo">Age:</label>

      <input type="text" id="form" v-model="age" name="age" placeholder="Your age..." />

      <label id="label" for="todo">School:</label>
      <input type="text" id="form" v-model="school" name="school" placeholder="Your school..." />

      <input type="submit" id="submitBtn" value="Submit" class="btn" />
    </form>
  </div>
</template>

<script>
export default {
  name: "InputForm",
  data() {
    return {
      name: "",
      age: "",
      school: "",
      id: 0
    };
  },
  methods: {
    addTodo() {
      const newTodo = {
        name: this.name,
        age: this.age,
        school: this.school,
        id: this.id
      };

      this.$emit("add-todo", newTodo);

      this.id = newTodo.id;

      this.name = this.age = this.school = "";
    },

    toggleForm() {
      this.$emit("toggle-form");
    }
  }
};
</script>