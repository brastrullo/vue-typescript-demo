<template>
  <Header :started="started" :clickHandler="getStarted" />
  <InsuranceSteps v-if="started" :msg="msg" />
  <StartScreen v-else :clickHandler="getStarted" />
  <NavFooter v-if="started" :currentStep="currentStep" />
</template>

<script lang="ts">
import { defineComponent } from "vue";
import StartScreen from "./components/StartScreen.vue";
import InsuranceSteps from "./components/InsuranceSteps.vue";
import Header from "./components/Header.vue";
import NavFooter from "./components/NavFooter.vue";

export default defineComponent({
  name: "App",
  data() {
    return {
      started: false,
      currentStep: 0
    };
  },
  components: {
    StartScreen,
    InsuranceSteps,
    Header,
    NavFooter
  },
  methods: {
    getStarted() {
      this.started = !this.started;
      this.currentStep = 1;
    }
  }
});
</script>

<style>
#app {
  font-family: Roboto, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 82px;
  font-size: 16px;
  box-sizing: border-box;
}
</style>
