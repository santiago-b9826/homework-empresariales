<template>
  <div>
    <div>
      <h1>MercadoLibre SB</h1>
      <input type="text" placeholder="Product" v-model="product">
      <input type="submit" value="Search" @click="searchProduct">
    </div>
    <div v-for="item in items" :key=item>
      <h4>{{ item.title }}</h4>
      <p>Precio:${{ item.price }}</p>
      <img :src="item.thumbnail" :alt="item.title">
    </div>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'Consume',
  data () {
    return {
      product: '',
      items: []
    }
  },
  methods: {
    searchProduct: function (e) {
      axios
        .get(`https://api.mercadolibre.com/sites/MCO/search?q=${this.product}`)
        .then(response => (this.items = response.data.results))
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h3 {
  margin: 40px 0 0;
}
</style>
