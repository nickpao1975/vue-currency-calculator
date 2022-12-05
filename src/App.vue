<script lang="ts">
import Counter from "@/components/Counter/Counter.vue";
import CurrencyCalculator from "@/components/CurrencyCalculator/CurrencyCalculator.vue";
import { defineComponent } from "vue";

export default defineComponent({
  components: { CurrencyCalculator, Counter },
});

defineComponent({
  components: {
    // "currency-calculator": CurrencyCalculator,
  },
});
</script>

<template>
  <Counter></Counter>
<!--  <currency-calculator></currency-calculator>-->

</template>

<style scoped></style>
