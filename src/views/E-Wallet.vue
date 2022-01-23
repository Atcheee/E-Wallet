<template>
  <ul>
    <li v-for="(data, items) in CreditCard" :key="items">
      <div id="Cards">
        <div class="card">
          <div class="card-front card-part">
            <img class="card-wifi" src="../assets/wifi.svg" alt="wifi icon" />
            <img class="card-chip" src="../assets/chip.svg" alt="card chip" />
            <img class="card-logo" src="" />
            <p class="card_number">data.content</p>
            <div class="card-space-75">
              <span class="card-label">CARDHOLDER NAME</span>
              <p class="card-info">{{ data.content }}</p>
            </div>
            <div>
              <div class="card-space-25">
                <span class="card-label">Valid Thru</span>
                <p class="card-info">{{ data.content }}</p>
              </div>
            </div>
          </div>
        </div>
      </div>
    </li>
    <AddCard v-show="false" @send="updateCardData" />
  </ul>
</template>

<script>
import AddCard from "./addCard.vue";
export default {
  components: { AddCard },
  props: ["cardDetail"],
  data() {
    return {
      CreditCard: "",
    };
  },
  methods: {
    updateCardData(data) {
      this.CreditCard = data;
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
  color: rgba(0, 0, 0, 1);
  letter-spacing: 1px;
}

.card-info {
  margin-bottom: 0;
  margin-top: 5px;
  font-size: 16px;
  line-height: 18px;
  color: rgb(0, 0, 0);
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