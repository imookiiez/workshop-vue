<template>
  <div class="container">
    <h1>All Product</h1>
    <hr>
    <div class='row'>
      <div class='col-md-3' v-for='item in data' :key='item.id'>
        <img :src='item.imgUrl' class='img-fluid center-block'>
        <h6 class="">{{item.name}}</h6>
        <hr>
        <h6>{{item.price}}</h6>
        <button class="btn btn-success" @click="addToCart(item)"> Add to Cart </button>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  props: ['data', 'cart'],
  methods: {
    addToCart: function (item) {
      if (this.cart.length > 0) {
        for (var i = 0; i < this.cart.length; i++) {
          if (item.id === this.cart[i].id) {
            this.cart[i].amount += 1
            break
          } else if (i === this.cart.length - 1) {
            this.cart.push(item)
            break
          }
        }
      } else {
        this.cart.push(item)
      }
    }
  }
}
</script>
<style scoped>

</style>
