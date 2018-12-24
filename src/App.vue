<template>
  <div id="app">
    <div class="shopping-list-actions" v-if="!editMode">
      <Button v-on:click="editMode = !editMode">Add Item</Button>
      <ClearButton v-on:click="clearList">Clear list</ClearButton>
    </div>
    <AddItemForm v-on:confirm="addToList" v-if="editMode"></AddItemForm>

    <ShoppingCart :items="items" v-on:purchased="tesable"/>
  </div>
</template>

<script>
import Header from './components/header/header.vue'
import AddItemForm from './components/add-item-form/AddItemForm.vue'
import ShoppingCart from './components/shopping-cart/shopping-cart.vue'
import ClearButton from './components/buttons/ClearButton.vue'
import Button from './components/buttons/Button.vue'

export default {
  name: 'app',
  components: {
    Header,
    AddItemForm,
    ShoppingCart,
    ClearButton,
    Button
  },
  data: function() {
    return {
      newItem: '',
      editMode: false,
      items: [
        {id: 1, name: 'namde', purchased: false, quantity: 1},
        {id: 2, name: 'ghjg', purchased: false, quantity: 1},
        {id: 3, name: 'ihoh', purchased: false, quantity: 1}
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
      this.editMode = false;
    },
    removeItem: function(item) {
      item.purchased = true;
    },
    clearList: function(){
      this.items = [];
    },
    tesable: function(item) {
      const index = this.items.indexOf(item);
      console.log('this is here', item, index, this.items[index].purchased);
      this.items[index].purchased = !this.items[index].purchased;
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
  width: 100%;
  height: 100%;
  margin: 10px auto;
  max-width: 300px;
}

.shopping-list-actions {
  display: flex;
  justify-content: space-between;
}
</style>
