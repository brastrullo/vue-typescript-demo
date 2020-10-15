<template>
  <section>
    <span class="main-icon">
      <img :alt="mainIconAltText" :src="mainIcon" />
    </span>
    <div></div>
    <h1>{{ header }}</h1>
    <List :list="list" />
    <button @click="clickHandler">{{ ctaText }}</button>
    <div class="signature">
      <img :alt="signatureAltText" :src="signatureIcon" />
      <span>{{ signatureText }}</span>
    </div>
  </section>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import List from "./IconTextList.vue";

export default defineComponent({
  name: "StartScreen",
  props: {
    clickHandler: Function,
    msg: String
  },
  components: {
    List
  },
  data() {
    return {
      header: "So what gives?",
      mainIcon: require("../assets/umbrella.svg"),
      mainIconAltText: "umbrella icon",
      signatureIcon: require("../assets/lightning.svg"),
      signatureIconAltText: require("../assets/lightning.svg"),
      signatureText: "Powered by Briza",
      ctaText: "Get Started"
    };
  }
});
</script>

<style scoped>
section {
  margin: 1.875em;
}

.main-icon {
  display: flex;
  width: 100px;
  height: 100px;
  background: #a8daff;
  border-radius: 50%;
  margin: auto;
}
.main-icon img {
  margin: auto;
  stroke: #0074d9;
}
h1 {
  font-weight: bold;
  font-size: 2.5em;
  color: #333333;
}

button {
  background: #71f79f;
  font-weight: bold;
  font-size: 1.125em;
  text-transform: uppercase;
  text-align: center;
  color: #333333;
  box-shadow: 0px 4px 4px rgba(0, 0, 0, 0.1);
  border: none;
  border-radius: 8px;
  width: 17.5em;
  height: 3.125em;
  margin: 4.375em 0 3.75em;
}

.signature {
  display: inline-flex;
  justify-content: center;
  align-content: center;
  margin: auto;
  text-align: center;
}
.signature img {
  stroke: #bdbdbd;
}
.signature span {
  margin: auto 0;
  margin-left: 8.89px;
  font-style: normal;
  font-weight: normal;
  font-size: 14.5465px;
  line-height: 17px;
  text-align: center;
  color: #bdbdbd;
}
</style>
