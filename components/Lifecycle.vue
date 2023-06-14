<script>
export default {
  data() {
    return {
      property: 'Example property.'
    }
  },
  computed: {
    propertyComputed() {
      return this.property
    }
  },
  mounted() {
    console.log(`At this point, vm.$el has been created and el has been
replaced.`);
    console.log(this.$el.textContent) // Example component.
  },
  beforeCreate() {
    console.log('At this point, events and lifecycle have been initialized.')
  },
  beforeMount() {
    console.log(`At this point, vm.$el has not been created yet.`)
  },
  created() {
    console.log('At this point, this.property is now reactive and propertyComputed update.')
    this.property = 'Example property updated.'
  },
  beforeDestroy() {
    console.log(`At this point, watchers, child components, and event listeners
have not been teared down yet.`)
// Perform the teardown procedure for exampleLeakyProperty.
// (In this case, effectively nothing)
    alert('Before Destroy');
  }
}
</script>

<template>
  <h1>Lifecycle</h1>
</template>

<style scoped>

</style>
