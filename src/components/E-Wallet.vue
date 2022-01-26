<template>
  <ul>
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
    <AddCard v-show="false" @send="updateCardData" />
  </ul>
</template>

<script>
import AddCard from "../views/addCard.vue";
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

<style lang="scss">

ul {
  li {
    display: grid;
    grid-auto-rows: auto;
    height: 70px;
  }
}
</style>