<template>
    <div class="col-8 container">
      <div class="todo-main col-6">
        <custom-header></custom-header>
        <hr />
        <form-todo @add-todo="addTodo"></form-todo>
        <todo-list :todos="todos" @delete-todo="deleteTodo" @edit-todo="editTodo"></todo-list>
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
    },
    deleteTodo(key){
      this.todos=this.todos.filter(item=>item.id!==key)
    },
    editTodo({id,text}){
      this.todos=this.todos.map(item=>{
        if (item.id===id){
          return {
            ...item,text:text
          }
        }
        return item;
      })
    }
  },
}
</script>
