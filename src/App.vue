<template>
  <div id="app">
    <Home
      v-if="currentView == 'Home'"
      :cards="cards"
      @changeCurrentView="currentView = 'AddCard'"
      @toggleActiveCard="toggleActiveCard"
    />
    <AddCard
      v-if="currentView == 'AddCard'"
      @card="saveCard"
      :cards="cards"
      @changeCurrentView="currentView = 'Home'"
    />
  </div>
</template>

<script>
import * as Views from "./views";
export default {
  components: {
    AddCard: Views.AddCard,
    Home: Views.Home,
  },
  data() {
    return {
      currentView: "Home",
      title: "E-WALLET",
      cardTitle: "Active card",
      cards: [
        // just some ready made cards to see how it looks
        {
          vendor: "bitcoin",
          cardNumber: "1223334444555555",
          cardHolder: "Someone Famous",
          expirationMonth: "2",
          expirationYear: "29",
          activeDisplayCard: false,
        },
        {
          vendor: "evil",
          cardNumber: "1234567891098765",
          cardHolder: "RAN DOM",
          expirationMonth: "09",
          expirationYear: "19",
          activeDisplayCard: false,
        },
      ],
    };
  },
  methods: {
    saveCard(card) {
      this.cards.push(card);
    },
    toggleActiveCard(index) {
      for (const cardActivity of this.cards) {
        if (cardActivity.activeDisplayCard === true) {
          cardActivity.activeDisplayCard = false;
        }
      }
      this.cards[index].activeDisplayCard =
        !this.cards[index].activeDisplayCard;
    },
  },
};
</script>

<style lang="scss">
@import url("https://fonts.googleapis.com/css2?family=Source+Sans+Pro:wght@300&display=swap");
@import url("https://fonts.googleapis.com/css2?family=PT+Mono&display=swap");

body {
  background-color: #eee;
  display: grid;
  place-items: center;
}

#app {
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  width: 400px;
  min-height: 800px;
  box-shadow: 0px 0px 32px rgba(0, 0, 0, 0.12);
  padding: 1rem;
  background-color: white;
  position: relative;
  overflow: hidden;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
}

button {
  font-size: 1.5rem;
  font-weight: 600;
  border: 1;
  border-radius: 8px;
  padding: 1rem;
  color: black;
  background-color: white;
}
</style>