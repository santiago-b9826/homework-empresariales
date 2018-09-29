<template>
  <div class="">
    <input type="text" placeholder="Product" v-model="product">
    <input type="submit" value="Search" @click="searchProduct">
    <div v-for="item in items" :key=item>
      <h3>{{ item.title }}</h3>
      <p>Precio:${{ item.price }}</p>
      <img :src="item.thumbnail" :alt="item.title">
    </div>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'HelloWorld',
  data () {
    return {
      product: '',
      items: []
    }
  },
  methods: {
    searchProduct: function (e) {
      axios
        .get(`https://api.mercadolibre.com/sites/MCO/search?q=${this.product}&limit=5`)
        .then(response => (this.items = response.data.results))
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
