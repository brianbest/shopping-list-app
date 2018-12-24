<template>
  <ul class="shopping-cart">
    <CartItem
      v-for="item in items"
      v-bind:key="item.id"
      v-bind:item="item"
      v-on:purchased="testThis"/>
  </ul>
</template>

<script>
import CartItem from './cart-item/cart-item.vue'

export default {
  name: 'ShoppingCart',
  components: {
    CartItem
  },
  props:{
    items: Array
  },
  methods: {
    testThis: function(item){
      console.log('hey!', item);
      this.$emit('purchased', item);
    }
  }
}
</script>

<style>
  .shopping-cart {
    padding: 0;
    margin: 0;
    display: flex;
    flex-direction: column;
  }

  .shopping-cart .cart-item {
    margin: 10px auto;
    width: 100%;
  }
</style>
