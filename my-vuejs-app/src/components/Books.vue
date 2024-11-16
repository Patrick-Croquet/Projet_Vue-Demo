<template>
    <div class="products">
      <h2>Books</h2>
      <ul>
        <li v-for="book in books" :key="book.id">
          {{ book.title }} - {{ book.author}}
        </li>
      </ul>
    </div>
</template>

<script>
    import axios from 'axios';

    export default {
    data() {
        return {
        books: [],
        };
    },
    mounted() {
        this.fetchData();
    },
    methods: {
        async fetchData() {
        try {
            const response = await axios.get('https://127.0.0.1:8000/api/books.jsonld');
            this.books = response.data.member;
        } catch (error) {
            console.error(error);
        }
        },
    },
    };
</script>

<style scoped>
.products {
    display: flex;
    align-items:center;

    background-image: url("images/fond.jpg");
    background-repeat: no-repeat;
    background-size: cover;
    padding: 2em;
    
    color: rgb(0, 0, 0);
    font-weight: bolder;
    font-size: 1.5em;
}

img
{
    vertical-align: middle; /* | top | bottom */
}

ul {
  list-style-type: none;
}
</style>


  
  