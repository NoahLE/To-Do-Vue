<template>
  <div class='ui centered card'>

    <!-- Todo list view (not editing) -->
    <div class="content"
         v-show="!isEditing">
      <div class='header'>
        {{ todo.title }}
      </div>
      <div class='meta'>
        {{ todo.project }}
      </div>

      <!-- Edit and delete icons -->
      <div class='extra content'>
        <span class='right floated'
              v-on:click="showForm">
          <i class='edit icon large hover-mouse'></i>
        </span>
        <span class='right floated'
              v-on:click="deleteTodo(todo)">
          <i class='trash icon large hover-mouse'></i>
        </span>
      </div>
    </div>

    <!-- Editing view -->
    <div class="content" v-show="isEditing">
      <div class='ui form'>
        <div class='field'>
          <label for="title">Title</label>
          <input id="title"
                 type='text'
                 v-model="todo.title">
        </div>
        <div class='field'>
          <label for="project">Project</label>
          <input id="project"
                 type='text'
                 v-model="todo.project">
        </div>
        <div class='ui two button attached buttons'>
          <button class='ui basic blue button'
                  v-on:click="hideForm">
            Save and close
          </button>
        </div>
      </div>
    </div>

    <!-- Pending or Completed buttons -->
    <div class='ui bottom attached green basic button'
         v-show="!isEditing &&todo.done" disabled>
      Completed
    </div>
    <div class='ui bottom attached red basic button'
         v-on:click="completeTodo(todo)" v-show="!isEditing && !todo.done">
      Pending
    </div>
  </div>

</template>

<script type="text/javascript">
  export default {
    props: ['todo'],
    data() {
      return {
        isEditing: false,
      };
    },
    methods: {
      completeTodo(todo) {
        this.$emit('complete-todo', todo);
      },
      deleteTodo(todo) {
        this.$emit('delete-todo', todo);
      },
      showForm() {
        this.isEditing = true;
      },
      hideForm() {
        this.isEditing = false;
      },
    },
  };
</script>

<style>
  .hover-mouse {
    cursor: pointer;
  }
</style>
