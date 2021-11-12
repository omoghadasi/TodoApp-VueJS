<template>
        <div class="todo-main__form w-100">
          <input type="text" class="form-control" placeholder="add more todo..." v-model="todoText"/>
          <button type="button" class="btn btn-outline-light w-25" @click="formHandler">ADD</button>
        </div>
</template>

<script>
export default {
  emits:['add-todo'],
  data() {
    return {
      todoText:''
    }
  },
  methods:{
    formHandler(){
      this.$emit('add-todo',this.todoText)
      this.todoText=''
    }
  }
}
</script>