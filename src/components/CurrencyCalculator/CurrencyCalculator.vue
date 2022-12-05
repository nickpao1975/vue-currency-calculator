<script>
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
      result: 0,
      history: []
    };
  },
  methods: {
    calculate() {
      if (this.conversion === "toDollar") {
        this.result = this.resultDollar
      } else {
        this.result = this.resultEuro
      }
      this.updateHistory();
    },
    updateHistory() {
      this.history.push(`Amount: ${this.amount}, exchange rate: ${this.exchangeRate}, result: ${this.result}`)
      if (this.history.length > 10) {
        this.history.shift()
      }
    },
    convertTo(event) {
      this.conversion = event.target.dataset.conversion;
      this.resetValues();
    },
    resetValues() {
      this.amount = 0;
      this.exchangeRate = 0;
      this.result = 0;
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
      <p>Dollar: {{ result }}</p>
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
      <p>Euro: {{ result }}</p>
    </template>
    <button @click="calculate">Calculate</button>

    <ul>
      <li v-for="item in history">{{ item }}</li>
    </ul>

  </main>
</template>

<style scoped></style>
