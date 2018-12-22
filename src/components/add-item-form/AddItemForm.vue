<template>
  <div class="">
    <input type="text" v-model="newItem" v-on:keydown.enter="confirm">
    <button :disabled="newItem == ''" v-on:click="confirm">Add item</button>
  </div>
</template>

<script>

export default {
  name: 'AddItemForm',
  data: function(){
    return {
      newItem: ''
    }
  },
  methods: {
    confirm: function () {
      //this.onConfirm(this.newItem)
      this.$emit('confirm', this.newItem);
    }
  }
}
</script>

<style>
  .title {
    font-size: 30px;
  }

</style>
