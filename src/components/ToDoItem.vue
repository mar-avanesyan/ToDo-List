<template>
  <ul>
    <li>
      <input type="checkbox" @click="$emit('changeCheckbox')" v-model="todo.completed" />
      <span v-show="!hide" :class="{ checkbox: todo.completed }" >{{ todo.title }}</span>
      <input v-show="hide" type="text" v-model="todo.title">
      <button @click="titleEdit">{{hide ? 'Save' : 'Edit'}}</button>
      <button @click="$emit('removeTodo')">x</button>
    </li>
  </ul>
</template>

<script>
export default {
  data() {
    return {
      hide: false,
    }
  },
  
  props: {
    todo: {
      type: Object,
      required: true,
    },
  },

  methods: {
    titleEdit () {
      this.hide = !this.hide;

      if (this.hide) {
        return
      }

      this.$emit('changeTitle', todo.title)
    
    }
  }

};
</script>

<style scoped>
.checkbox {
  text-decoration-line: line-through;
}

li {
  border: 1px solid #ccc;
  display: flex;
  justify-content: space-between;
  padding: 3px;
  width: 500px;
  margin: 0 auto;
}
</style>