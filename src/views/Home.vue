<template>
  <div class="E-Wallet">
    <h1>E-WALLET</h1>
    <p>ACTIVE CARD</p>
    <EWallet :cards="cards" @toggleActiveCard="toggleActiveCard" />
    <button @click="$emit('changeCurrentView')">ADD A NEW CARD</button>
  </div>
</template>

<script>
import EWallet from "../components/E-Wallet.vue";
export default {
  components: { EWallet },
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

h1 {
  font-family: "Source Sans Pro", sans-serif;
  font-size: 35px;
  font-style: normal;
  font-weight: 700;
  line-height: 35px;
  letter-spacing: 0em;
  text-align: center;
}

p,
button {
  font-family: "PT Mono";
}

p {
  font-size: 0.8rem;
}
</style>