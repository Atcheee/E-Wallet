<template>
  <div id="app">
    <Home v-if="currentView == 'Home'" @send="updateCardData" />
    <footer>
      <button v-if="currentView == 'Home'" @click="currentView = 'AddCard'">
        ADD A NEW CARD
      </button>
    </footer>
    <AddCard v-if="currentView == 'AddCard'" @send="updateCardData" />
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
      currentView: "",
      CreditCard: "",
    };
  },
  beforeMount() {
    this.currentView = "Home";
    // localStorage.clear(); // uncomment if you want to clear the cards
  },
  methods: {
    updateCardData(data) {
      this.CreditCard = data;
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
footer {
  display: flex;
  flex-direction: column;
  button {
    font-size: 1.5rem;
    font-weight: 600;
    border: 1;
    border-radius: 8px;
    padding: 1rem;
    color: black;
    background-color: white;
  }
}
</style>