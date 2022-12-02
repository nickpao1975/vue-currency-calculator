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
      <input type="text" />
    </div>
    <div>
      <input type="text" />
    </div>
  </main>
</template>

<style scoped></style>
