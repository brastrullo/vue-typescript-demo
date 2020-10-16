<template>
  <main role="main" class="insurance-steps-list">
    <section
      v-for="step in steps"
      :disabled="step.id !== currentStep"
      :key="step.id"
    >
      <ListItemBold :n="step.id" :text="step.text" />
      <article>
        <InputRadio
          v-if="step.id === 1"
          :items="insuranceItems"
          :inital-value="''"
          :step="step"
          :input-handler="inputHandler"
          :update-step="updateStep"
        />
        <InputText
          type="text"
          v-else-if="step.id === 2"
          placeholder="Hoop Heaven"
        />
        <InputText
          type="text"
          v-else-if="step.id === 3"
          placeholder="(111)111-1111"
        />
        <input type="text" v-else-if="step.id === 4" placeholder="state" />
        <InputRadio
          v-if="step.id === 5"
          :items="designItems"
          :value="''"
          :step="step"
          :input-handler="inputHandler"
        />
        <p v-if="step.id === 6">Does your business provide design services?</p>
        <InputRadio
          v-if="step.id === 6"
          :items="designItems"
          :value="''"
          :step="step"
          :input-handler="inputHandler"
        />
        <input v-else-if="step.id === 7" />
        <button v-if="step.id === currentStep && step.id !== 7">OK</button>
        <button v-if="step.id === currentStep && step.id === 7">
          Get Quotes
        </button>
      </article>
    </section>
  </main>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import InputText from "./InputText.vue";
import InputRadio from "./InputRadio.vue";
import ListItemBold from "./ListItemBold.vue";

export default defineComponent({
  name: "InsuranceSteps",
  prop: {
    buttonHandler: Function,
    updateStep: Function,
    currentStep: Number
  },
  components: {
    ListItemBold,
    InputText,
    InputRadio
  },
  data() {
    return {
      steps: [
        {
          id: 1,
          text: "What type of insurance are you looking for?",
          name: "insurance",
          value: ""
        },
        {
          id: 2,
          text: "What’s the name of your business?",
          name: "business",
          value: ""
        },
        {
          id: 3,
          text: "What’s the phone number?",
          name: "phone",
          value: ""
        },
        {
          id: 4,
          text: "What state do you operate from?",
          name: "state",
          value: ""
        },
        {
          id: 5,
          text: "Do you do your own design?",
          name: "design",
          value: ""
        },
        {
          id: 6,
          text: "Include building coverage?",
          name: "coverage",
          value: ""
        },
        {
          id: 7,
          text: "When did your business begin?",
          name: "date",
          value: ""
        }
      ],
      insuranceItems: [
        {
          id: 1,
          name: "Professional Liability",
          description: "Erros & Omissions (E&O insurance)",
          icon: require("../assets/insurance-professional.svg"),
          value: "pro"
        },
        {
          id: 2,
          name: "General Liability",
          description: "Help mitigate against loss (CGL insurance)",
          icon: require("../assets/insurance-general.svg"),
          value: "gen"
        },
        {
          id: 3,
          name: "Business Owner’s Policy",
          description: "The complete package (BOP)",
          icon: require("../assets/insurance-business.svg"),
          value: "bus"
        },
        {
          id: 4,
          name: "Cyber",
          description: "Internet-bsed risks (CLIC)",
          icon: require("../assets/insurance-cyber.svg"),
          value: "cyb"
        }
      ],
      designItems: [
        {
          id: 1,
          name: "Yes",
          description: "We do designs in-house",
          icon: require("../assets/design-yes.svg"),
          value: "yes"
        },
        {
          id: 2,
          name: "No",
          description: "We’re gonna need some assistance",
          icon: require("../assets/design-no.svg"),
          value: "no"
        }
      ],
      buildingCoverageItems: [
        {
          id: 1,
          name: "Yes",
          description: "",
          icon: require("../assets/coverage-yes.svg"),
          value: "yes"
        },
        {
          id: 2,
          name: "No",
          description: "",
          icon: require("../assets/coverage-no.svg"),
          value: "no"
        }
      ]
    };
  },
  methods: {
    inputHandler(e: Event | null) {
      if (e === null) {
        throw e;
      } else {
        console.log(e);
      }
    }
  }
});
</script>

<style scoped>
main {
  /* padding-left: 0; */
  margin: 0;
  display: flex;
  flex-flow: column nowrap;
  align-items: center;
  justify-content: center;
}
.insurance-steps-list {
  margin-bottom: 3.75em;
}

article {
  margin-top: 2.5em;
  margin-bottom: 3.125em;
}
section[disabled="true"] p {
  opacity: 0.25;
}
section[disabled="true"] .list-icon {
  opacity: 0.25;
}
</style>
