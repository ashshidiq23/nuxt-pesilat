<script>

export default {
  props: {
    className: String,
  }
}
</script>

<template>
  <button type="button" :class="`btn bg-success ${className}`">Click Me</button>
</template>

<style scoped>

</style>
