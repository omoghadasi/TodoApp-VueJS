<template>
    <div class="col-8 container">
      <div class="todo-main col-6">
        <custom-header></custom-header>
        <hr />
        <form-todo @add-todo="addTodo"></form-todo>
        <todo-list :todos="todos"></todo-list>
      </div>
    </div>
</template>

<style>
#app{
  width: 100%;
}
</style>

<script>
import HeaderVue from './components/Header.vue';
import FormAddTodoVue from './components/FormAddTodo.vue';
import TodoListVue from './components/TodoList.vue';

export default{
    data(){
      return{
        todos:[]
      }
    },
  components:{
    'custom-header': HeaderVue,
    'form-todo': FormAddTodoVue,
    'todo-list': TodoListVue,
  },
  methods: {
    addTodo(text){
      this.todos.push({
        id:Date.now(),
        done:false,
        text
      })
    }
  },
}
</script>
