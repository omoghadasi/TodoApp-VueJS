<template>
  <div class="todo-main__todos w-100 pt-3 pb-3 mb-3">
    <ul class="nav nav-tabs mb-2" id="myTab" role="tablist">
      <li class="nav-item" role="presentation">
        <button
          class="nav-link active"
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
      <li class="nav-item" role="presentation">
        <button
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
        <TodoVue></TodoVue>
      </div>
      <div
        class="tab-pane fade"
        id="done"
        role="tabpanel"
        aria-labelledby="done-tab"
      >
        <TodoVue></TodoVue>
      </div>
    </div>
  </div>
</template>

<script>
import TodoVue from "./Todo.vue";
export default {
  components: {
    TodoVue,
  },
};
</script>
