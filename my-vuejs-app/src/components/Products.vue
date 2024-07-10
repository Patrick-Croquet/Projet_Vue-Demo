<template>
    <div class="products">
      <h2>Produits</h2>
      <ul>
        <li v-for="product in products" :key="product.id">
          <img :src="`images/products/${product.image}`" width="125" height="auto" />  
          {{ product.name }} - {{ product.price }}€
        </li>
      </ul>
    </div>
</template>

<script>
    import axios from 'axios';

    export default {
    data() {
        return {
        products: [],
        };
    },
    mounted() {
        this.fetchData();
    },
    methods: {
        async fetchData() {
        try {
            const response = await axios.get('http://localhost:5173/data.json');
            this.products = response.data;
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


  
  