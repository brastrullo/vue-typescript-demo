<template>
  <Header :started="started" :clickHandler="getStarted" />
  <transition name="pageslide">
    <InsuranceStepsScreen
      v-if="started"
      :current-step="currentStep"
      :update-step="updateStep"
    />
    <StartScreen v-else :click-handler="getStarted" />
  </transition>
  <transition name="navslide">
    <NavFooter v-if="started" :current-step="currentStep" />
  </transition>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import StartScreen from "./components/StartScreen.vue";
import InsuranceStepsScreen from "./components/InsuranceStepsScreen.vue";
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
      currentStep: 0
    };
  },
  components: {
    StartScreen,
    InsuranceStepsScreen,
    Header,
    NavFooter
  },
  methods: {
    getStarted() {
      this.started = !this.started;
      this.currentStep = 1;
    },
    updateStep(step: number) {
      this.currentStep = step;
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
button:focus {
  outline: none;
}
.pageslide-enter-active,
.pageslide-leave-active {
  transition: transform 0.5s ease 0.2s;
}
.pageslide-enter-from,
.pageslide-leave-to {
  transform: translateY(100%);
}

.navslide-enter-active,
.navslide-leave-active {
  transition: transform 0.3s ease 0.2s;
}
.navslide-enter-from,
.navslide-leave-to {
  transform: translateY(100%);
}
</style>
