<template>
  <div id="addCard">
    <header>
      <h1>
        ADD A NEW <br />
        BANK CARD
      </h1>
      <p>NEW CARD</p>
    </header>
    <div id="Cards">
      <div class="card">
        <div class="card-front card-part" :class="bgcolor">
          <img class="card-wifi" src="../assets/wifi.svg" alt="wifi icon" />
          <img class="card-chip" src="../assets/chip.svg" alt="card chip" />
          <img class="card-logo" src="" />
          <p class="card_number">{{ userInput.cardNumber }}</p>
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
          <select name="month" id="month" v-model="userInput.month">
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
          <select name="year" id="year" v-model="userInput.year">
            <option>21</option>
            <option>22</option>
            <option>23</option>
            <option>24</option>
            <option>25</option>
            <option>26</option>
          </select>
        </p>

        <p>
          <label for="vendor"></label>
          <select id="vendor" name="vendor" v-model="bgcolor">
            <option disabled selected value>-- select an option --</option>
            <option
              v-for="backgroundClass in this.colorClasses"
              :key="backgroundClass"
            >
              {{ backgroundClass }}
            </option>
          </select>
        </p>
        <button @click="addCard" >ADD CARD</button>
      </form>
    </main>
  </div>
</template>

<script>

function IdGenerator() {
  return Math.floor(Math.random() * Math.pow(10, 25)).toString();
}

function perseveredData(data) {
  localStorage.setItem("cardData", JSON.stringify(data));
}

export default {
  props: ['AddCardView'],
  data() {
    return {
      userInput: {
        cardNumber: null,
        cardHolder: null,
        month: "",
        year: "",
      },
      content: "",
      Cards: [],
      bgcolor: "defaultColor",
      colorClasses: [
        "BITCOIN INC",
        "NINJA BANK",
        "BLOCKCHAIN INC",
        "EVIL CORP",
      ], // not sure if this should be in userInput or not, leaving it here for now
    };
  },
  methods: {
    submit() {
      this.$emit("send", { ...this.userInput });
    },
    expirationDate() { // combinds the expiration date and the year (plus a slash symbol in the middle)
      return this.userInput.month + "/" + this.userInput.year;
    },
    addCard() {
      this.Cards.push({
        id: IdGenerator(),
        content:
          this.userInput.cardNumber +
          " " +
          this.userInput.cardHolder +
          " " +
          this.expirationDate(),
      });
      this.content = "";
      perseveredData(this.Cards);
    },
        addTodo(){
      this.Cards.push({
        id: IdGenerator(),
        content: this.content,
        done: false
      })
      this.content = ''
      perseveredData(this.Cards)
    },
  },
  created() {
    let savedCardData = localStorage.getItem("cardData");
    if (savedCardData) {
      this.Cards = JSON.parse(savedCardData);
    }
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

#Cards {
  display: inline-block;
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
  background-repeat: no-repeat;
  background-position: center;
  background-size: cover;
  border-radius: 8px;
}

.defaultColor {
  background: gray;
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

.card_number {
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

.BITCOIN.INC {
  background-color: #ffae34;
}
.NINJA.BANK {
  background-color: #222222;
}
.BLOCKCHAIN.INC {
  background-color: #8b58f9;
}
.EVIL.CORP {
  background-color: #f33355;
}
</style>