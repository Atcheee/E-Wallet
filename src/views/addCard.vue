<template>
  <div id="addCard">
    <header>
      <h1>
        ADD A NEW <br />
        BANK CARD
      </h1>
      <p>NEW CARD</p>
    </header>
    <div id="cards">
      <div class="card">
        <div class="card-front card-part">
          <img class="card-wifi" src="../assets/wifi.svg" alt="wifi icon" />
          <img class="card-chip" src="../assets/chip.svg" alt="card chip" />
          <img class="card-logo" src="" />
          <p class="card_numer">{{ userInput.cardNumber }}</p>
          <div class="card-space-75">
            <span class="card-label">CARDHOLDER NAME</span>
            <p class="card-info">{{ userInput.cardHolder }}</p>
          </div>
          <div>
            <div class="card-space-25">
              <span class="card-label">Valid Thru</span>
              <p class="card-info">{{ expirationDate() }}</p>
            </div>
          </div>
        </div>
      </div>
    </div>
    <main>
      <form action="" method="post" @submit.prevent="submit">
        <p>
          <label for="cardNumber">CARD NUMBER</label>
          <br />
          <input
            id="cardNumber"
            type="number"
            name="cardNumber"
            pattern=".{,16}"
            v-model="userInput.cardNumber"
          />
        </p>

        <p>
          <label for="cardHolder">CARDHOLDER</label>
          <br />
          <input
            id="cardHolder"
            type="text"
            name="cardHolder"
            v-model="userInput.cardHolder"
          />
        </p>

        <p>
          <label for="month">MONTH</label>
          <br />
          <input
            id="month"
            type="number"
            name="month"
            v-model="userInput.month"
          />
        </p>

        <p>
          <label for="year">YEAR</label>
          <br />
          <input type="number" name="year" v-model="userInput.year" />
        </p>

        <p>
          <label for="vendor"></label>
          <select id="vendor" name="vendor">
            <option disabled selected value>-- select an option --</option>
            <option>BITCOIN INC</option>
            <option>NINJA BANK</option>
            <option>BLOCK CHAIN INC</option>
            <option>EVIL CORP</option>
          </select>
        </p>
        <button>ADD CARD</button>
      </form>
    </main>
  </div>
</template>

<script>
export default {
  data() {
    return {
      userInput: {
        errors: [],
        cardNumber: null,
        cardHolder: null,
        month: "",
        year: "",
        numberSum: 0,
      },
    };
  },
  methods: {
    submit() {
      this.$emit("send", { ...this.userInput });
    },
    expirationDate() {
      return this.userInput.month + "/" + this.userInput.year;
    },
  },
};
</script>

<style lang="scss" scoped>
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

.card {
  width: 320px;
  height: 190px;
  -webkit-perspective: 600px;
  -moz-perspective: 600px;
  perspective: 600px;
}

.card-part {
  box-shadow: 1px 1px #aaa3a3;
  top: 0;
  position: absolute;
  z-index: 1000;
  left: 0;
  display: inline-block;
  width: 320px;
  height: 190px;
  background: gray;
  background-repeat: no-repeat;
  background-position: center;
  background-size: cover;
  border-radius: 8px;
}

.card-front {
  padding: 18px;
}

.card-black-line {
  margin-top: 5px;
  height: 38px;
  background-color: #303030;
}

.card-logo {
  height: 32px;
  position: absolute;
  top: 18px;
  right: 18px;
}

.card-wifi {
  height: 40px;
  left: 0;
  position: absolute;
  margin-left: 1.5rem;
  margin-top: -0.5rem;
}

.card-chip {
  height: 30px;
  left: 0;
  position: absolute;
  margin: 1.5rem;
}

.card_numer {
  display: block;
  width: 100%;
  word-spacing: 4px;
  font-size: 20px;
  letter-spacing: 2px;
  color: #fff;
  text-align: center;
  margin-bottom: 20px;
  margin-top: 20px;
}

.card-space-75 {
  width: 75%;
  float: left;
}

.card-space-25 {
  width: 25%;
  float: left;
}

.card-label {
  font-size: 10px;
  text-transform: uppercase;
  color: rgba(255, 255, 255, 0.8);
  letter-spacing: 1px;
}

.card-info {
  margin-bottom: 0;
  margin-top: 5px;
  font-size: 16px;
  line-height: 18px;
  color: #fff;
  letter-spacing: 1px;
  text-transform: uppercase;
}

form {
  button {
    color: white;
    background-color: black;
    font-size: 18px;
  }
}
</style>