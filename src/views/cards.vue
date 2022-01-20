<template>
  <div id="cards">
    <div class="card">
      <div class="card-front card-part">
        <img class="card-wifi" src="../assets/wifi.svg" alt="wifi icon" />
        <img class="card-chip" src="../assets/chip.svg" alt="card chip" />
        <img class="card-logo" src="../assets/bitcoin.svg" alt="vendicator" />
        <p class="card_numer">{{ cardNumber }}</p>
        <div class="card-space-75">
          <span class="card-label">CARDHOLDER NAME</span>
          <p class="card-info">{{ cardHolder }}</p>
        </div>
        <div>
          <span class="card-label">Valid Thru</span>
          <p class="card-info">{{ fullExpirationDate() }}</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      cardNumber: 1234 + " " + 5678 + " " + 9101 + " " + 1123,
      cardHolder: "FirstName LastName",
      month: 6,
      year: 26,
    };
  },
  methods: {
    fullExpirationDate() {
      return this.month + "/" + this.year;
    },
  },
};
</script>

<style scoped>
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
  background: #ffae34;
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
  height: 30px;
  left: 0;
  position: absolute;
}

.card-chip {
  height: 30px;
  left: 0;
  position: absolute;
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
</style>