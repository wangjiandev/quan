<template>
  <svg class="q-icon">
    <use :xlink:href="`#i${name}`"></use>
  </svg>
</template>
<script>
  export default {
    props: ['name']
  }
</script>
<style>
  .q-icon {
    width: 1em;
    height: 1em;
  }
</style>
