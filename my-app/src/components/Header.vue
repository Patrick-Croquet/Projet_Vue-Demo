<script setup>
    import HelloWorld from './HelloWorld.vue'
</script>

<template>
    <nav>
        <RouterLink to="/">Home</RouterLink>
        <RouterLink to="/about">About</RouterLink>
        <RouterLink to="/contact">Contact</RouterLink>
    </nav>

    <div class="wrapper">
      <HelloWorld msg="You did it!" />
    </div>

    <div class="container mx-auto py-12">
        <h1 class="text-3xl font-bold text-gray-800">Mon application Vue3.js avec Tailwind</h1>
        <button class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded">Bouton Tailwind</button>
    </div>
</template>

