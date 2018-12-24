<template>
  <div class="">
    <input type="text" v-model="newItem" v-on:keydown.enter="confirm">
    <Button :disabled="newItem == ''" v-on:click="confirm">Add item</Button>
  </div>
</template>

<script>
import Button from '../buttons/Button.vue';

export default {
  name: 'AddItemForm',
  components: {
    Button
  },
  data: function(){
    return {
      newItem: ''
    }
  },
  methods: {
    confirm: function () {
      this.$emit('confirm', this.newItem);
      this.newItem = "";
    }
  }
}
</script>

<style>
  .title {
    font-size: 30px;
  }

</style>
