<template>
  <button v-on:click="clicked" class="shopping-list-button">
    <slot></slot>
  </button>
</template>
<script>

export default {
  name: 'Button',
  methods: {
    clicked: function(params) {
      this.$emit('click')
    }
  }
}
</script>

<style>
  .shopping-list-button {
    border: 0;
    border-radius: 4px;
    background: linear-gradient(135deg, rgba(60,158,255,1) 0%, rgba(48,79,254,1) 100%);
    color: #fff;
    padding: 10px;
  }

  .shopping-list-button:focus{
    outline: none;
  }
</style>
