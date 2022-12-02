<script>
import { defineComponent } from "vue";

export default defineComponent({
  name: "CurrencyCalculator",
  data() {
    return {
      amount: 0,
      exchangeRate: 0,
    };
  },
});
</script>

<template>
  <header>
    <h1>Currency Calculator</h1>
    <nav>
      <ul>
        <li>Euro -> Dollar</li>
        <li>Dollar -> Euro</li>
      </ul>
    </nav>
  </header>
  <main>
    <div>
      <label for="amount">Amount (Euro): </label>
      <input type="text" id="amount" />
    </div>
    <div>
      <label for="exchangeRate">Exchange rate: </label>
      <input type="text" id="exchangeRate" />
    </div>
  </main>
</template>

<style scoped></style>
