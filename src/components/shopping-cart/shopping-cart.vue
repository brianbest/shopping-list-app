<template>
  <ul class="shopping-cart">
    <CartItem
      v-for="item in items"
      v-bind:key="item.id"
      v-bind:item="item"/>
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
  data: function() {
    return {

    }
  },
  methods: {
  }
}
</script>

<style>

</style>
