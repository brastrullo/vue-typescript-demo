<template>
  <footer>
    <span>{{ currentStep }}/7</span>
    <nav>
      <button v-bind:disabled="currentStep === 1">
        <img class="prev-icon" :alt="prevIconAltText" :src="prevIcon" />
      </button>
      <button v-bind:disabled="currentStep === 7">
        <img class="next-icon" :alt="nextIconAltText" :src="nextIcon" />
      </button>
    </nav>
  </footer>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: "NavFoter",
  props: {
    currentStep: Number
  },
  data() {
    return {
      nextIcon: require("../assets/next.svg"),
      nextIconAltText: "increment icon",
      prevIcon: require("../assets/prev.svg"),
      prevIconAltText: "decrement button"
    };
  }
});
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
footer {
  display: flex;
  flex-flow: row nowrap;
  height: 3.75em;
  width: 100vw;
  position: fixed;
  z-index: 999;
  bottom: 0;
  left: 0;
  background: #0074d9;
  box-shadow: 0px -1px 4px rgba(0, 0, 0, 0.25);
  justify-content: space-between;
  align-items: center;
  padding: 0 1rem;
  box-sizing: border-box;
}
span {
  font-weight: bold;
  font-size: 1.125em;
  color: #ffffff;
}
nav {
  display: flex;
  flex-flow: row nowrap;
  align-items: center;
}
button {
  background: #ffffff;
  border: none;
  height: 2.286em;
  width: 2.286em;
  border-radius: 2.5px;
}
button:disabled {
  opacity: 0.8;
}
button + button {
  margin-left: 0.5rem;
}
</style>
