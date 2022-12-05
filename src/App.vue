<script lang="ts">
import CurrencyCalculator from "@/components/CurrencyCalculator/CurrencyCalculator.vue";
import { defineComponent } from "vue";

export default defineComponent({
  components: {
    "currency-calculator": CurrencyCalculator,
  },
});
</script>

<template>
  <currency-calculator></currency-calculator>

</template>

<style scoped></style>
