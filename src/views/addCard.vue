<template>
  <div id="addCard">
    <header>
      <h1>
        ADD A NEW <br />
        BANK CARD
      </h1>
      <p>NEW CARD</p>
      <Cards :card="card" />
    </header>
    <main>
      <form action="" method="post" @submit.prevent="submit">
        <p>
          <label for="cardNumber">CARD NUMBER</label>
          <br />
          <input
            id="cardNumber"
            type="number"
            name="cardNumber"
            v-model="card.cardNumber"
            oninput="javascript: if (this.value.length > this.maxLength) this.value = this.value.slice(0, this.maxLength);"
            maxlength="16"
          />
        </p>

        <p>
          <label for="cardHolder">CARDHOLDER</label>
          <br />
          <input
            id="cardHolder"
            type="text"
            name="cardHolder"
            v-model="card.cardHolder"

          />
        </p>

        <p>
          <label for="month">MONTH</label>
          <br />
          <select name="month" id="month" v-model="card.expirationMonth">
            <option>1</option>
            <option>2</option>
            <option>3</option>
            <option>4</option>
            <option>5</option>
            <option>6</option>
            <option>7</option>
            <option>8</option>
            <option>9</option>
            <option>10</option>
            <option>11</option>
            <option>12</option>
          </select>
        </p>

        <p>
          <label for="year">YEAR</label>
          <br />
          <select name="year" id="year" v-model="card.expirationYear">
            <option>21</option>
            <option>22</option>
            <option>23</option>
            <option>24</option>
            <option>25</option>
            <option>26</option>
          </select>
        </p>

        <p>
          <label for="vendor">CHOOSE A VENDOR</label>
          <br />
          <select id="vendor" name="vendor" v-model="card.vendor">
            <option disabled selected value>-- select an option --</option>
					<option value="" disabled selected hidden></option>
					<option value="bitcoin">BITCOIN INC</option>
					<option value="ninja">NINJA BANK</option>
					<option value="blockchain">BLOCKCHAIN INC</option>
					<option value="evil">EVIL CORP</option>
          </select>
        </p>
      <button @click="$emit('changeCurrentView'), submit()" :cards="cards" type="submit">ADD CARD</button>
      </form>
    </main>
  </div>
</template>

<script>
// function perseveredData(data) {
//   localStorage.setItem("cardData", JSON.stringify(data));
// }
import Cards from "../components/cards.vue";
export default {
  props: { cards: Array },
  components: { Cards },
  data() {
    return {
      card: {
        cardNumber: "",
        cardHolder: "",
        expirationMonth: "",
        expirationYear: "",
        vendor: "",
        activeDisplayCard: false,
      },
    };
  },
  methods: {
    submit() {
      this.$emit("card", { ...this.card });
    },
  },
  // created() {
  //   let savedCardData = localStorage.getItem("cardData");
  //   if (savedCardData) {
  //     this.Cards = JSON.parse(savedCardData);
  //   }
  // },
  // beforeMount() {
  //   this.$emit("send", { ...this.Cards });
  // },
};
</script>

<style lang="scss">
@import url("https://fonts.googleapis.com/css2?family=Source+Sans+Pro:wght@200&display=swap");
* {
  box-sizing: border-box;
  font-family: "Source Sans Pro";
  font-style: normal;
  font-weight: 200;
  font-display: swap;
}

html,
body {
  margin: 0;
  padding: 0;
  height: 100%;
  width: 100%;
}
</style>