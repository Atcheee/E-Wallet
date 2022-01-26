<template>
  <div>
    <div class="card" v-if="DisplayCard !== null">
      <div class="card-front card-part" :class="DisplayCard.content.cardColor">
        <img class="card-wifi" src="../assets/wifi.svg" alt="wifi icon" />
        <img class="card-chip" src="../assets/chip.svg" alt="card chip" />
        <img class="card-logo" src="" />
        <p class="card_number">{{ DisplayCard.content.cardNumber }}</p>
        <div class="card-space-75">
          <span class="card-label">CARDHOLDER NAME</span>
          <p class="card-info">{{ DisplayCard.content.cardHolder }}</p>
        </div>
        <div>
          <div class="card-space-25">
            <span class="card-label">Valid Thru</span>
            <p class="card-info">{{ DisplayCard.content.expirationDate }}</p>
          </div>
        </div>
      </div>
    </div>
    <br>
    <br>
    <br>
    <section v-for="(data, items) in CreditCard" :key="items" :id="items" @click="DisplayCard = data">
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
    </section>
    <AddCard v-show="false" @send="updateCardData" />
  </div>
</template>

<script>
import AddCard from "../views/addCard.vue";
export default {
  components: { AddCard },
  data() {
    return {
      CreditCard: "",
      DisplayCard: null,
      viewCard: true,
    };
  },
  methods: {
    updateCardData(data) {
      this.CreditCard = data;
    },
    showCard() {
      this.viewCard = true;
    },
  },
};
</script>

<style lang="scss">
section {
  display: grid;
  grid-auto-rows: auto;
  height: 70px;
  list-style-type: none;
  justify-content: center;
}
.card {
  display: inline-block;
}
</style>