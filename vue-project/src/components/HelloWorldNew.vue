<script>
    export default {
    props: {
        message: String
    },
    data() {
        return {
        title: 'Mon application Vue.js',
        message: 'Bienvenue !',
        count: 0
        }
    },
    methods: {
        increment() {
        this.count++
        },
        reverseMessage() {
        this.message = this.message.split('').reverse().join('');
        }
    }
    }
</script>

<template>
    <div>
      <h1>{{ title }}</h1>
      <p>{{ message }}</p>
      <button class="btn btn-primary" @click="reverseMessage">Inverser le message</button>
      <button class="btn btn-primary" v-on:click="increment">Ajouter</button>
      <span>Count: {{ count }}</span>
    </div>
</template>
  