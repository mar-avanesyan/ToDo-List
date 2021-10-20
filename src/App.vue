<template>
  <div>
    <h1>ToDo List</h1>
    <input type="text" v-model="title" />
    <button @click="addtodo(title)">Add ToDo</button>
    <ToDoList
      :todos="todos"
      @changeCheckbox="changeCheckbox"
      @removeTodo="removeTodo"
      @changeTitle="changeTitle"
    />
  </div>
</template> 

<script>
import ToDoList from "./components/ToDoList.vue";

export default {
  data() {
    return {
      title: "",
      todos: [],
    };
  },
  components: {
    ToDoList,
  },
  methods: {
    changeTitle({ index, title }) {
      this.todos[index].title = title;
    },

    changeCheckbox(index) {
      this.todos[index].completed = !this.todos[index].completed;
    },

    addtodo(param) {
      this.todos.push({
        title: param,
        completed: false,
      });
      this.title = "";
    },

    removeTodo(index) {
      this.todos.splice(index, 1);
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
