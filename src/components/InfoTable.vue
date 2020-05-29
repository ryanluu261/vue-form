<template>
  <div>
    <table>
      <tr>
        <th>Full name</th>
        <th>Age</th>
        <th>School</th>
        <th>Actions</th>
      </tr>

      <tr v-for="(todo, index) in todos" v-bind:key="todo.id">
        <td>{{todo.name}}</td>
        <td>{{todo.age}}</td>
        <td>{{todo.school}}</td>
        <td>
          <button
            @click="funnyEmit(todo, index)"
            class="del"
            style="background: blue; float: left"
          >Edit</button>
          <button @click="$emit('del-todo', todo.id)" class="del">Bye</button>
        </td>
      </tr>
    </table>
  </div>
</template>

<script>
export default {
  name: "InfoTable",
  props: {
    todos: {
      type: Array
    }
  },
  methods: {
    funnyEmit(item, index) {
      this.$emit("edit-todo", { item, index });
    }
  }
};
</script>