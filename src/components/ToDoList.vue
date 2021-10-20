<template>
  <ToDoItem
    v-for="(todo, index) in todos"
    :key="index"
    :todo="todo"
    @changeCheckbox="$emit('changeCheckbox', index)"
    @removeTodo="$emit('removeTodo', index)"
    @changeTitle="(title) =>
      $emit('changeTitle', {
        title,
        index,
      })
    "
  />
</template>

<script >
import ToDoItem from "./ToDoItem.vue";
export default {
  props: ["todos"],
  components: {
    ToDoItem,
  },
};
</script>
