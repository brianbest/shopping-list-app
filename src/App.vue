<template>
  <div id="app">
    <Header size="title">Shopping List</Header>
    <div class="">
      <input type="text" v-model="newItem" v-on:keydown.enter="addToList">
      <button :disabled="newItem == ''" v-on:click="addToList">Add item</button>
    </div>
    <button v-on:click="clearList">Clear list</button>
    <ul>
      <li
      v-for="item in items"
      v-on:click="removeItem(item)"
      v-bind:key="item.id"
      :class="{purchased: item.purchased}">{{item.name}}</li>
    </ul>
  </div>
</template>

<script>
import Header from './components/header/header.vue'

export default {
  name: 'app',
  components: {
    Header
  },
  data: function() {
    return {
      newItem: '',
      items: [
        {id: 1, name: 'namde'}
      ]
    }
  },
  methods: {
    addToList: function () {
      if (this.newItem == '') {
        return;
      }
      var x = {id: this.items.length + 1, name: this.newItem, purchased: false};
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
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.purchased{
  color: green;
}
</style>
