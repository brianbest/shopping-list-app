<template>
  <li class="cart-item" v-on:click="purchasedToggle" v-bind:class="{purchased: this.item.purchased}">
    <h4>{{item.name}}</h4>
    <span>{{item.quantity}}</span>
    <div class="checkbox"></div>
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
      classObject: {
        purchased: this.item.purchased
      }
    }
  },
  methods: {
    purchasedToggle: function(){
      console.log('i hear you', this.cartItem)
      this.$emit('purchased', this.item);
    }
  }
}
</script>

<style>
.cart-item {
  color: #fff;
  display: grid;
  grid-template-columns: 1fr 20px auto;
  list-style: none;
  background: linear-gradient(135deg, rgba(189,102,222,1) 0%, rgba(79,70,206,1) 100%);
  max-width: 300px;
  padding: 10px;
  border-radius: 4px;
  box-sizing: border-box;
}

.cart-item.purchased {
  opacity: 0.5;
  text-decoration: line-through;
}

.cart-item h4 {
  margin: 0;
}

.cart-item .checkbox {
  width: 20px;
  height: 20px;
  border: 1px solid #fff;
  border-radius: 100px;
}
</style>
