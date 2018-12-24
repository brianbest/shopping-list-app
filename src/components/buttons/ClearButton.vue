<template>
  <Button class="clear-button">
    <slot></slot>
  </Button>
</template>
<script>
import Button from './Button.vue';

export default {
  name: 'ClearButton',
  components: {
    Button
  }
}
</script>

<style scoped>
  /* .clear-button {
    color: blue;
  } */
</style>
