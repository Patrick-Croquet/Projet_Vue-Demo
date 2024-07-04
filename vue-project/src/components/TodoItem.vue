<script>
  export default {
    props: {
      task: String
    },
    data() {
      return {
        completed: false
      }
    },
    methods: {
      remove() {
        this.$emit('remove', this.task)
      }
    }
  }
</script>

<template>
    <div class="container">
      <h1>Mon application Vue.js avec Bootstrap</h1>
      <button class="btn btn-primary">Bouton Bootstrap</button>
    </div>

    <div class="todo-item">
      <input type="checkbox" v-model="completed" />
      <span>{{ task }}</span>
      <button @click="remove">Supprimer</button>
    </div>
</template>
  
<style scoped>
  .todo-item {
    display: flex;
    align-items: center;
  }
  
  .todo-item input[type="checkbox"] {
    margin-right: 10px;
  }
  
  .todo-item .completed {
    text-decoration: line-through;
  }
</style>