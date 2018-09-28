<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <div v-for="item in items" :key=item>
      {{ item.title }} ||
      {{ item.thumbnail }} ||
      {{ item.price }}
    </div>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'HelloWorld',
  data () {
    return {
      items: []
    }
  },
  mounted () {
    axios
      .get('https://api.mercadolibre.com/sites/MCO/search?q=play')
      .then(response => (this.items = response.data.results))
  },
  props: {
    msg: String
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
