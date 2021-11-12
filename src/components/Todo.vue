<template>
  <div class="todo d-flex justify-content-between align-items-center mt-1 p-2">
    <span class="text">
      {{ todo.text}}
    </span>
    <div class="action">
      <div
        class="btn-group btn-group-sm"
        role="group"
        aria-label="Basic mixed styles example"
      >
        <button type="button" class="btn btn-success">{{ todo.done?'Undone':'Done' }}</button>
        <button type="button" class="btn btn-warning">Edit</button>
        <button type="button" class="btn btn-danger">Delete</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props:{
    todo:{
      type:Object,
    }
  }
}

</script>
