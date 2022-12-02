<script>
import { defineComponent } from "vue";

export default defineComponent({
  name: "CurrencyCalculator",
  data() {
    return {
      amount: 0,
      exchangeRate: 0,
      conversion: "toDollar",
    };
  },
});
</script>

<template>
  <header>
    <h1>Currency Calculator</h1>
    <nav>
      <ul>
        <li><a @click="conversion = 'toDollar'" href="#">Euro -> Dollar</a></li>
        <li><a @click="conversion = 'toEuro'" href="#">Dollar -> Euro</a></li>
      </ul>
    </nav>
  </header>
  <main>
    <template v-if="conversion === 'toDollar'">
      <div>
        <label for="amount">Amount (Euro): </label>
        <input type="text" id="amount" v-model="amount" />
      </div>
      <div>
        <label for="exchangeRate">Exchange rate: </label>
        <input type="text" id="exchangeRate" v-model="exchangeRate" />
      </div>
      <p>Dollar: {{ amount * exchangeRate }}</p>
    </template>
    <template v-else>
      <div>
        <label for="amount">Amount (Dollar): </label>
        <input type="text" id="amount" v-model="amount" />
      </div>
      <div>
        <label for="exchangeRate">Exchange rate: </label>
        <input type="text" id="exchangeRate" v-model="exchangeRate" />
      </div>
      <p>
        Euro:
        {{
          isNaN(amount / exchangeRate) || !isFinite(amount / exchangeRate)
            ? 0
            : amount / exchangeRate
        }}
      </p>
    </template>
  </main>
</template>

<style scoped></style>
