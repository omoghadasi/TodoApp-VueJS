<template>
  <div class="todo-main__todos w-100 pt-3 pb-3 mb-3">
    <ul class="nav nav-tabs mb-2" id="myTab" role="tablist">
      <li @click="statusDone=false" class="nav-item" role="presentation">
        <button :class="{active:!statusDone}"
          class="nav-link"
          id="undone-tab"
          data-bs-toggle="tab"
          data-bs-target="#undone"
          type="button"
          role="tab"
          aria-controls="undone"
          aria-selected="true"
        >
          Undone
        </button>
      </li>
      <li @click="statusDone=true" class="nav-item" role="presentation">
        <button :class="{active:statusDone}"
          class="nav-link"
          id="done-tab"
          data-bs-toggle="tab"
          data-bs-target="#done"
          type="button"
          role="tab"
          aria-controls="done"
          aria-selected="false"
        >
          done
        </button>
      </li>
    </ul>
    <div class="tab-content" id="myTabContent">
      <div
        class="tab-pane fade show active"
        id="undone"
        role="tabpanel"
        aria-labelledby="undone-tab"
      >
        <TodoVue v-for="item in filterTodos(todos.value)" :todo="item" :key="item.id"></TodoVue>
      </div>
    </div>
  </div>
</template>

<script>
import TodoVue from "./Todo.vue";
export default {
  data(){
    return{
      statusDone:false
    }
  },
  inject:['todos'],
  components: {
    TodoVue,
  },
  methods:{
    filterTodos(todo){
      return todo.filter(item=>item.done===this.statusDone)
    }
  }
};
</script>
