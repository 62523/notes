<script setup>

</script>
<template>
  <section class="Calendar">
    <b-calendar block locale="en-US"></b-calendar>
  </section>

</template>

<script>
  export default {
    data() {
      return {
        state: 'disabled'
      }
    },
    computed: {
      disabled() {
        return this.state === 'disabled'
      },
      readonly() {
        return this.state === 'readonly'
      }
    }
  }
</script>
<style scoped>

</style>
