<template>
  <li id="todo-list-item" class="list-group-item">
    {{ todo.text }}
      <button @click="$emit('remove', todo.id)" class="close" aria-label="Close">
          <span aria-hidden="true">&times;</span>
      </button>
  </li>
</template>

<script>
export default {
  props: {
    todo: {
      type: Object,
      required: true
    }
  }
}
</script>

<style>

  #todo-list-item{
    	line-height: 1.4;
      color: rgb(61, 61, 61);
      font-size: 24px;
      font-family: 'Caveat', cursive;
  }
  .close:focus {
    outline: none !important;
}

</style>