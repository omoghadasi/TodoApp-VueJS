<template>
  <div class="todo d-flex justify-content-between align-items-center mt-1 p-2" v-if="editMode===false">
    <span class="text">
      {{ todo.text }}
    </span>
    <div class="action">
      <div
        class="btn-group btn-group-sm"
        role="group"
        aria-label="Basic mixed styles example"
      >
        <button type="button" class="btn btn-success">{{ todo.done?'Undone':'Done' }}</button>
        <button type="button" class="btn btn-warning" @click="enableEdit">Edit</button>
        <button type="button" class="btn btn-danger" @click="$emit('delete-todo',todo.id)">Delete</button>
      </div>
    </div>
  </div>
  <div class="todo d-flex justify-content-between align-items-center mt-1 p-2" v-if="editMode===true">
    <span class="text">
      <input type="text" v-model="todoText">
    </span>
    <div class="action">
      <div
        class="btn-group btn-group-sm"
        role="group"
        aria-label="Basic mixed styles example"
      >
        <button type="button" class="btn btn-warning" @click="editTodo">Edit</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  emits:['delete-todo','edit-todo'],
  props:{
    todo:{
      type:Object,
    }
  },
  data(){
    return{
      editMode:false,
      todoText:''
    }
  },
  methods:{
    enableEdit(){
      this.editMode=true
      this.todoText=this.todo.text
    },
    editTodo(){
      this.editMode=false
      this.$emit('edit-todo',{id: this.todo.id,text: this.todoText})
      this.todoText='';
    }
  }
}

</script>
