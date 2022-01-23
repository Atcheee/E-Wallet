<template>
  <div>
    <ul>
      <AddCardView v-for="data in creditCard" :key="data" />
    </ul>
  </div>
</template>

<script>
import AddCardView from "./addCard.vue";
export default {
  components: { AddCardView },
  props: ["creditCard"],
  data() {
    return {};
  },
};
</script>

<style>
</style>