<template>
<section>
  <h1>Our Products</h1>
    <v-select :options="options"></v-select>
  <div>
    <ul>
      <li v-for="product in products">
        <nuxt-link :to="'/product/' + product.id"> {{product.title}}</nuxt-link>
      </li>
    </ul>
  </div>
</section>
</template>

<script>
import axios from '~/plugins/axios'

export default {
  data () {
    return {
      posts: [],
      options: ["Product", "Description", "Post", "Price", "Department "]
    }
  },
  async asyncData () {
    const {data} = await axios.get('https://jsonplaceholder.typicode.com/posts') //' https://localhost:5000/ Want to connect here to read the Flask API 
    console.log(data.id)
    return {products:data}
  },
  async filterProducts(id) {
    // Filter each product by ID
    const {products} = await axios.get('https://jsonplaceholder.typicode.com/posts')
  }
}
</script>