<template>
  <div id="app">
    <button class="btn" @click="isVisiblePopup = !isVisiblePopup">Enter your info!</button>
    <div v-if="isVisiblePopup" class="mask-popup">
      <InputForm id="popup" v-on:add-todo="addTodo" v-on:toggle-form="toggleForm" />
    </div>
    <InfoTable id="table" :todos.sync="todos" v-on:del-todo="deleteTodo" v-on:edit-todo="editTodo" />
    <EditForm
      v-if="isVisibleEdit"
      id="popup"
      v-on:change-todo="changeTodo"
      v-on:toggle-edit="toggleEdit"
    />
  </div>
</template>

<script>
import InputForm from "./components/InputForm";
import InfoTable from "./components/InfoTable";
import EditForm from "./components/EditForm";

export default {
  name: "App",

  components: {
    InputForm,
    InfoTable,
    EditForm
  },

  data() {
    return {
      todofk: [
        {
          name: "99",
          age: 12,
          school: "HKK"
        }
      ],
      isVisiblePopup: false,
      isVisibleEdit: false,
      oldTodo: {},
      index: 0
    };
  },
  computed: {
    todos() {
      return this.todofk;
    }
  },
  methods: {
    addTodo(newTodo) {
      newTodo.id = this.todos.length;

      this.todos = [...this.todos, newTodo];

      this.isVisiblePopup = !this.isVisiblePopup;
    },
    toggleForm() {
      if (this.isVisiblePopup) {
        this.isVisiblePopup = false;
      }
    },

    toggleEdit() {
      if (this.isVisibleEdit) {
        this.isVisibleEdit = false;
      }
    },
    deleteTodo(id) {
      this.todos = this.todos.filter(todo => todo.id !== id);
    },
    editTodo({ item, index }) {
      this.isVisibleEdit = true;
      this.oldTodo = item;
      this.index = index;
    },
    changeTodo(newTodo) {
      this.todos[this.index] = newTodo;

      this.isVisibleEdit = !this.isVisibleEdit;
      console.log(this.todos);
      console.log(this.index);
      console.log(typeof this.todos[this.index]);
    }
  },
  watch: {
    todos: {
      deep: true,
      handler: function(val, oldVal) {
        console.log(val, oldVal + "hihihi");
        //todoa
      }
    }
  }
};
</script>


