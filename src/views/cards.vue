<template>
  <div>
    <ul>
      <AddCardView v-for="data in Cards" :key="data" />
    </ul>
  </div>
</template>

<script>
import AddCardView from "./addCard.vue";
export default {
  components: { AddCardView },
  props: ["CreditCard"],
  data() {
    return {
      Cards: [1],
    };
  },
};
</script>

<style>
</style>