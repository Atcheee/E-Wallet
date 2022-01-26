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
          <img class="card-logo" />
          <p class="card_number">{{ userInput.cardNumber }}</p>
          <p class="card_number" v-if="userInput.cardNumber == ''">
            **** **** **** ****
          </p>
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
            v-model="userInput.cardHolder"
            @input="onlyLetters"
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
          <label for="vendor">CHOOSE A VENDOR</label>
          <br />
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
      </form>
    </main>
    <footer>
      <button @click="addCard(); reload()">ADD CARD</button>
    </footer>
  </div>
</template>

<script>
function perseveredData(data) {
  localStorage.setItem("cardData", JSON.stringify(data));
}

export default {
  components: {},
  props: ["AddCardView"],
  data() {
    return {
      userInput: {
        cardNumber: "",
        cardHolder: null,
        month: "",
        year: "",
      },
      Cards: [],
      bgcolor: "defaultColor",
      colorClasses: [
        "BITCOIN INC",
        "NINJA BANK",
        "BLOCKCHAIN INC",
        "EVIL CORP",
      ], // not sure if this should be in userInput or not, leaving it here for now
      srcImg: [
        "../assets/bitcoin.svg",
        "../assets/ninja.svg",
        "../assets/blockchain.svg",
        "../assets/evil.svg",
      ],
    };
  },
  methods: {
    submit() {
      this.$emit("send", { ...this.Cards });
    },
    expirationDate() {
      return this.userInput.month + "/" + this.userInput.year; // combinds the expiration date and the year (plus a slash symbol in the middle)
    },
    addCard() {
      this.Cards.push({
        content: {
          cardNumber: this.userInput.cardNumber,
          cardHolder: this.userInput.cardHolder,
          expirationDate: this.expirationDate(),
          cardColor: this.bgcolor,
          id: this.Cards.length,
        },
      });
      perseveredData(this.Cards);
    },
    onlyLetters() {
      this.userInput.cardHolder = this.userInput.cardHolder
        .replaceAll(/[^a-zA-Z\s]+/g, "")
        .toUpperCase();
    },
    reload() {
      window.location.reload();
    },
  },
  created() {
    let savedCardData = localStorage.getItem("cardData");
    if (savedCardData) {
      this.Cards = JSON.parse(savedCardData);
    }
  },
  beforeMount() {
    this.$emit("send", { ...this.Cards });
  },
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
  font-size: 15px;
  letter-spacing: 2px;
  color: #fff;
  text-align: left;
  margin-bottom: 20px;
  margin-top: 20px;
  padding-left: 60px;
}

.card-space-75 {
  float: left;
  padding-top: 35px;
}

.card-space-25 {
  float: right;
  padding-top: 35px;
}

.card-label {
  font-size: 9px;
  text-transform: uppercase;
  color: rgba(255, 255, 255, 0.8);
  letter-spacing: 1px;
}

.card-info {
  padding-bottom: 10px;
  margin-top: 5px;
  font-size: 16px;
  line-height: 18px;
  color: #fff;
  letter-spacing: 1px;
  text-transform: uppercase;
  position: absolute;
  bottom: 0;
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