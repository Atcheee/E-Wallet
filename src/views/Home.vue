<template>
  <div class="E-Wallet">
    <div class="activeCard" v-if="activeCard">
      <h1>E-WALLET</h1>
      <p>ACTIVE CARD</p>
      <EWallet
        :cards="cards"
        @toggleActive="toggleActiveCard"
      />
    </div>
    <!-- <EWallet @click="makeCardActive(card)" :cards="cards" /> -->
    <footer>
      <button @click="$emit('changeCurrentView')">ADD A NEW CARD</button>
    </footer>
  </div>
</template>

<script>
import EWallet from "../components/E-Wallet.vue";
export default {
  components: { EWallet },
  props: { cards: Array },
  data() {
    return {
      activeCard: this.cards,
    };
  },
  methods: {
    toggleActiveCard(item) {
      this.$emit("toggleActiveCard", item);
    },
  },
  computed: {
    // filterActiveCard() {
    //   return this.cards.filter((card) => card != this.activeCard);
    // },
  },
};
</script>

<style>
button {
  position: absolute;
  bottom: 0;
  left: 0;
  width: 100%;
}
.cardsOnTop {
  display: grid;
  grid-auto-rows: auto;
  list-style-type: none;
  justify-content: center;
}
</style>