<template>
  <div>
    <div v-for="(card, item) in cards" :key="card.cardNumber[item]">
      <Card v-if="card.activeDisplayCard" :card="card" :index="item" />
    </div>
    <div v-for="(card, item) in cards" :key="card.cardNumber">
      <Card
        :card="card"
        @activeCard="toggleActiveCard"
        :index="item"
        class="cardsOnTop"
      />
    </div>
  </div>
</template>

<script>
import Card from "./cards.vue";
export default {
  components: { Card },
  props: { cards: Array },
  data() {
    return {};
  },
  methods: {
    toggleActiveCard(index) {
      this.$emit("toggleActiveCard", index);
    },
  },
};
</script>

<style lang="scss">
.cardsOnTop {
  display: grid;
  grid-auto-rows: auto;
  height: 80px;
}
</style>