<template>
  <div>
    <span v-if="started" class="header-title">
      <img class="header-icon" :alt="headerIconAltText" :src="headerIcon" />
      <span>{{ headerText }}</span>
    </span>
    <button @click="() => {started ? clickHandler() : ''} ">
      <img class="close-icon" :alt="closeIconAltText" :src="closeIcon" />
    </button>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: "Header",
  props: {
    started: Boolean,
    clickHandler: Function
  },
  data() {
    return {
      currentStep: 1,
      headerIcon: require("../assets/umbrella.svg"),
      headerIconAltText: "header icon",
      closeIcon: require("../assets/close.svg"),
      closeIconAltText: "close button",
      headerText: "Umbrella Hub"
    };
  }
});
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
div {
  display: flex;
  flex-flow: row nowrap;
  box-sizing: border-box;
  width: 100vw;
  justify-content: flex-start;
  align-items: center;
  padding: 2.563em 1.875em 0;
  top: 0;
  right: 0;
  position: fixed;
}
.header-title {
  display: flex;
  flex-flow: row nowrap;
  justify-content: flex-start;
  align-items: center;
}
.header-title span {
  font-size: 0.903em;
  color: #0074d9;
}
.header-icon {
  height: 1.618em;
  margin-right: 0.539em;
}

button {
  right: 1.875em;
  position: absolute;
  background: none;
  padding: 0;
  border: none;
}
.close-icon {
  margin: auto;
}
</style>
