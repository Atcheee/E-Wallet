<template>
  <ul>
    <Cards v-for="data in Cards" 
    :key="data.id"
    :Cards="data"/>
  </ul>
</template>

<script>
// import CardDetails from './E-Wallet.vue'
export default {
  // components: {CardDetails},
  props: ['Cards']
}
</script>

<style>

</style>