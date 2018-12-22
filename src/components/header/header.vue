<template>
  <h2 class="header" :class="size">
    <slot></slot>
  </h2>
</template>

<script>

export default {
  name: 'Header',
  props:{
    size: String
  }
}
</script>

<style>
  .title {
    font-size: 30px;
  }

</style>
