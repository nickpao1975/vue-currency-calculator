<script lang="ts">
import CalculatorNavigation from "@/components/CalculatorNavigation/CalculatorNavigation.vue";
import { defineComponent } from "vue";

export default defineComponent({
  name: "CurrencyCalculator",
  components: {
    navigation: CalculatorNavigation,
  },
  data() {
    return {
      amount: 0,
      exchangeRate: 0,
      conversion: "toDollar",
    };
  },
  methods: {
    convertTo(event) {
      this.conversion = event.target.dataset.conversion;
    },
    resetValues() {
      this.amount = 0;
      this.exchangeRate = 0;
      this.conversion = "toDollar";
    },
  },
  computed: {
    resultDollar() {
      const result = this.amount * this.exchangeRate;
      const invalid = isNaN(result);
      return invalid ? 0 : result;
    },
    resultEuro() {
      const result = this.amount / this.exchangeRate;
      const invalid = isNaN(result) || !isFinite(result);
      return invalid ? 0 : result;
    },
  },
});
</script>

<template>
  <header>
    <h1>Currency Calculator</h1>
    <navigation @click="convertTo"></navigation>
  </header>
  <main @keyup.esc="resetValues">
    <template v-if="conversion === 'toDollar'">
      <div>
        <label for="amount">Amount (Euro): </label>
        <input @keyup.shift.alt.e="convertTo" data-conversion="toEuro" type="text" id="amount" v-model="amount" />
      </div>
      <div>
        <label for="exchangeRate">Exchange rate: </label>
        <input type="text" id="exchangeRate" v-model="exchangeRate" />
      </div>
      <p>Dollar: {{ resultDollar }}</p>
    </template>
    <template v-else>
      <div>
        <label for="amount">Amount (Dollar): </label>
        <input @keyup.shift.alt.d="convertTo" data-conversion="toDollar" type="text" id="amount" v-model="amount" />
      </div>
      <div>
        <label for="exchangeRate">Exchange rate: </label>
        <input type="text" id="exchangeRate" v-model="exchangeRate" />
      </div>
      <p>Euro: {{ resultEuro }}</p>
    </template>
  </main>
</template>

<style scoped></style>
