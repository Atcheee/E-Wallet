<template>
  <div>
    <li v-for="(data, items) in CreditCard" :key="items">
      <div id="Cards">
        <div class="card">
          <div class="card-front card-part" :class="data.content.cardColor">
            <img class="card-wifi" src="../assets/wifi.svg" alt="wifi icon" />
            <img class="card-chip" src="../assets/chip.svg" alt="card chip" />
            <img class="card-logo" src="" />
            <p class="card_number">{{ data.content.cardNumber }}</p>
            <div class="card-space-75">
              <span class="card-label">CARDHOLDER NAME</span>
              <p class="card-info">{{ data.content.cardHolder }}</p>
            </div>
            <div>
              <div class="card-space-25">
                <span class="card-label">Valid Thru</span>
                <p class="card-info">{{ data.content.expirationDate }}</p>
              </div>
            </div>
          </div>
        </div>
      </div>
    </li>
  </div>
</template>

<script>
// import AddCardView from "../views/addCard.vue";
export default {
  // components: { AddCardView },
  props: ["CreditCard"],
  data() {
    return {
      Cards: [],
    };
  },
  methods: {
    updateCardData(data) {
      this.CreditCard = data;
    },
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