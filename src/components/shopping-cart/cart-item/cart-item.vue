<template>
  <li class="cart-item" v-on:click="purchasedToggle" v-bind:class="classObject">
    {{cartItem.name}}
  </li>
</template>

<script>

export default {
  name: 'CartItem',
  props: {
    item: {
      type: Object,
      default: function () {
        return { id: '', name: '',  purchased: false}
      }
    }
  },
  data: function() {
    return {
      cartItem: this.item,
      classObject: {
        purchased: this.cartItem.purchased
      }
    }
  },
  methods: {
    purchasedToggle: function(){
      console.log('i hear you', this.cartItem)
      this.cartItem.purchased = true;
    }
  }
}
</script>

<style>
.cart-item {
  list-style: none;
}

.cart-item.purchased {
  opacity: 0.5;
  text-decoration: line-through;
}
</style>
