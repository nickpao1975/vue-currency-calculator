<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: "CalculatorNavigation",
});
</script>

<template>
  <nav class="navbar" role="navigation" aria-label="main navigation">
    <div class="navbar-menu">
      <div class="navbar-start">
        <a class="navbar-item" href="#" data-conversion="toDollar">
          Euro&nbsp;<i class="fa fa-arrow-right"></i>&nbsp;Dollar
        </a>
        <a class="navbar-item" href="#" data-conversion="toEuro">
          Dollar&nbsp;<i class="fa fa-arrow-right"></i>&nbsp;Euro
        </a>
      </div>
    </div>
  </nav>
</template>

<style scoped></style>
