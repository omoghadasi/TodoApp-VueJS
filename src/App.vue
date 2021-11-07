<script>
import HeaderVue from './components/Header.vue';
import FormAddTodoVue from './components/FormAddTodo.vue';
import TodoListVue from './components/TodoList.vue';

export default{
    data(){
      return{
        todos:[
          {
            id:1,
            done:false,
            text:'this is todo'
          },
          {
            id:2,
            done:false,
            text:'this is todo'
          },
          {
            id:3,
            done:false,
            text:'this is todo'
          },
        ]
      }
    },
  components:{
    'custom-header': HeaderVue,
    'form-todo': FormAddTodoVue,
    'todo-list': TodoListVue,
  }
}
</script>

<template>
    <div class="col-8 container">
      <div class="todo-main col-6">
        <custom-header></custom-header>
        <hr />
        <form-todo></form-todo>
        <todo-list :todos="todos"></todo-list>
      </div>
    </div>
</template>

<style>
#app{
  width: 100%;
}
</style>
