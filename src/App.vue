<template>
  <div class="col-8 container">
    <div class="todo-main col-6">
      <custom-header></custom-header>
      <hr/>
      <form-todo @add-todo="addTodo"></form-todo>
      <todo-list></todo-list>
    </div>
  </div>
</template>

<style>
#app {
  width: 100%;
}
</style>

<script>
import {computed} from "vue";
import HeaderVue from './components/Header.vue';
import FormAddTodoVue from './components/FormAddTodo.vue';
import TodoListVue from './components/TodoList.vue';

export default {
  data() {
    return {
      todos: []
    }
  },
  components: {
    'custom-header': HeaderVue,
    'form-todo': FormAddTodoVue,
    'todo-list': TodoListVue,
  },
  methods: {
    addTodo(text) {
      this.todos.push({
        id: Date.now(),
        done: false,
        text
      })
    },
    deleteTodo(id) {
      this.todos = this.todos.filter(item => item.id !== id)
    },
    editTodo({id, text}) {
      this.todos = this.todos.map(item => {
        if (item.id === id) {
          return {
            ...item, text: text
          }
        }
        return item;
      })
    },
    doneTodo(id) {
      this.todos = this.todos.map(item => {
        if (item.id === id) {
          return {
            ...item,done: !item.done
          }
        }
        return item;
      })
    }
  },
  provide() {
    return {
      todos: computed(() => this.todos),
      deleteTodo: this.deleteTodo,
      editTodo: this.editTodo,
      doneTodo: this.doneTodo
    }
  }
}
</script>
