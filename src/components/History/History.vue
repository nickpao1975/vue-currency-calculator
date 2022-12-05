<script>
import { defineComponent } from "vue";

export default defineComponent({
  name: "History",
  props: {
    conversion: String,
    history: {
      type: Object,
      required: true,
    },
  },
  data() {
    return {
      calculationHistory: [],
    };
  },
  watch: {
    history() {
      this.updateHistory();
    },
  },
  computed: {
    amountCurrencySymbol() {
      return this.conversion === "toDollar" ? "EUR" : "USD";
    },
    resultCurrencySymbol() {
      return this.conversion === "toDollar" ? "USD" : "EUR";
    },
  },
  methods: {
    updateHistory() {
      this.calculationHistory.push(
        {
          ...this.history, // -> you can use this Spread operator or comment out the following 4 lines
          // id: this.history.id,
          // amount: this.history.amount,
          // exchangeRate: this.history.exchangeRate,
          // result: this.history.result,
          amountCurrencySymbol: this.amountCurrencySymbol,
          resultCurrencySymbol: this.resultCurrencySymbol,
        },
      );
    },
  },
});

</script>

<template>
  <table>
    <thead>
    <tr>
      <th>Amount</th>
      <th>Exchange rate</th>
      <th>Result</th>
    </tr>
    </thead>
    <tbody>
    <tr v-for="item in calculationHistory" :key="item.id">
      <td>{{ item.amount }}&nbsp;{{ item.amountCurrencySymbol }}</td>
      <td>{{ item.exchangeRate }}</td>
      <td>{{ item.result }}&nbsp;{{ item.resultCurrencySymbol }}</td>
    </tr>
    </tbody>
  </table>
</template>

<style scoped>

</style>
