<template>
  <Header :started="started" :clickHandler="getStarted" />
  <transition name="pageslide">
    <InsuranceSteps
      v-if="started"
      :stepData="stepData"
      :buttonHandler="setStepData"
      :currentStep="currentStep"
    />
    <StartScreen v-else :clickHandler="getStarted" />
  </transition>
  <transition name="navslide">
    <NavFooter v-if="started" :currentStep="currentStep" />
  </transition>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import StartScreen from "./components/StartScreen.vue";
import InsuranceSteps from "./components/InsuranceSteps.vue";
import Header from "./components/Header.vue";
import NavFooter from "./components/NavFooter.vue";

interface Step {
  step: number;
  name: string;
  value: string;
}

export default defineComponent({
  name: "App",
  data() {
    return {
      started: false,
      currentStep: 0,
      stepData: [
        { step: 1, name: "insurance", value: "" },
        { step: 2, name: "business", value: "" },
        { step: 3, name: "phone", value: "" },
        { step: 4, name: "state", value: "" },
        { step: 5, name: "design", value: "" },
        { step: 6, name: "coverage", value: "" },
        { step: 7, name: "start", value: "" }
      ]
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
    },
    setStepData(obj: Step) {
      alert(obj);
      // this.stepData[obj.step - 1].value = obj.value;
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
  background: #f9f9f9;
  margin-top: 105px;
  font-size: 16px;
  box-sizing: border-box;
}
.pageslide-enter-active,
.pageslide-leave-active {
  transition: transform 0.5s ease;
}
.pageslide-enter-from {
  transform: translateY(0%);
}
.pageslide-leave-to {
  transform: translateY(100%);
}

.navslide-enter-active,
.navslide-leave-active {
  transition: transform 0.5s ease;
}
.navslide-enter-from {
  transform: translateY(0%);
}
.navslide-leave-to {
  transform: translateY(150vh);
}
</style>
