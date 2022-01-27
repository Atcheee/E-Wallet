<template>
  <div>
    <section>
      <div v-for="(card, item) in cards" :key="card.cardNumber">
          <Card v-if="card.active" :card="card" :index="item" />
          <Card :card="card" @activeCard="toggleActiveCard" :index="item" class="cardsOnTop" />
      </div>
    </section>
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
    toggleActiveCard(item) {
      this.$emit("toggleActiveCard", item);
    },
  },
};
</script>

<style lang="scss" scoped>
.cardsOnTop {
  display: grid;
  grid-auto-rows: auto;
  height: 70px;
  list-style-type: none;
  justify-content: center;
}
</style>