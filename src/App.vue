<template>
  <div id="app">
    <cart :cart="cart"></cart>
    <book-shelves :data="list" :cart="cart"></book-shelves>
  </div>
</template>
<script>
import BookShelves from '@/components/BookShelves.vue'
import Cart from '@/components/Cart.vue'
import axios from 'axios'
export default {
  data () {
    return {
      list: [],
      cart: []
    }
  },
  components: {
    BookShelves,
    Cart
  },
  async created () {
    var data = await axios.get('https://us-central1-cloud-fn-1c36b.cloudfunctions.net/getItems')
    console.log(data.data)
    this.list = data.data
  },
  methods: {

  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
#nav {
  padding: 30px;
}

#nav a {
  font-weight: bold;
  color: #2c3e50;
}

#nav a.router-link-exact-active {
  color: #42b983;
}
</style>
