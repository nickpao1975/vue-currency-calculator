<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: "Counter",
  data() {
    return {
      counter: 2,
      secondCounter: 0
    }
  },
  methods: {
    inc2() {
      this.secondCounter++;
    },
    inc() {
      this.counter++;
    },
    dec() {
      this.counter--;
    },
  },
  computed: {
    even() {
      console.log('eval even')
      return this.counter % 2 === 0;
    },
    uneven() {
      console.log('eval uneven')
      return this.secondCounter % 2 !== 0;
    },
  }
});
</script>

<template>
  <h1>Counter Application</h1>
  <div>
    <p>Current Counter Value: <strong>{{ counter }}</strong></p>
    <p>Second Counter Value: <strong>{{ secondCounter }}</strong></p>

    <div style="margin-top: 2rem">
      <button @click="inc">Increase</button>
      <button @click="inc2">Increase second counter</button>
      <button :disabled="even" @click="dec">Decrease</button>

      <div> Uneven? {{ uneven }}</div>
    </div>
  </div>
</template>

<style scoped>

</style>
