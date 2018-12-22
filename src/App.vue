<template>
  <div id="app">
    <Header size="title">Shopping List</Header>
    <AddItemForm v-on:confirm="addToList"></AddItemForm>
    <button v-on:click="clearList">Clear list</button>
    <ShoppingCart :items="items" />
  </div>
</template>

<script>
import Header from './components/header/header.vue'
import AddItemForm from './components/add-item-form/AddItemForm.vue'
import ShoppingCart from './components/shopping-cart/shopping-cart.vue'

export default {
  name: 'app',
  components: {
    Header,
    AddItemForm,
    ShoppingCart
  },
  data: function() {
    return {
      newItem: '',
      items: [
        {id: 1, name: 'namde'},
        {id: 2, name: 'ghjg'},
        {id: 3, name: 'ihoh'}
      ]
    }
  },
  methods: {
    addToList: function (itemName) {
      if (itemName == '') {
        return;
      }
      var x = {id: this.items.length + 1, name: itemName, purchased: false};
      this.items.push(x);
      this.newItem = '';
    },
    removeItem: function(item) {
      item.purchased = true;
    },
    clearList: function(){
      this.items = [];
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
