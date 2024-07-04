<script>
    export default {
        props: {
            taskText: String,
            isDone: Boolean
        }
    }
</script>

<template>
    <li>
      <input type="checkbox" v-bind:checked="isDone" />
      <span>{{ taskText }}</span>
    </li>
</template>
  

  