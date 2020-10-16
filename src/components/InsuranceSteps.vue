<template>
  <ul class="insurance-steps-list">
    <li
      v-for="step in steps"
      :disabled="step.id !== currentStep"
      :key="step.id"
    >
      <ListItemBold :n="step.id" :text="step.text" />
      <section>
        <ul v-if="step.id === 1">
          <BoxListItem
            @click="buttonHandler"
            v-for="item in insuranceItems"
            :value="item.id"
            :key="item.id"
            :icon="item.icon"
            :name="item.name"
            :description="item.description"
          />
        </ul>
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
        <ul v-if="step.id === 5">
          <BoxListItem
            v-for="item in designItems"
            :key="item.id"
            :icon="item.icon"
            :name="item.name"
            :description="item.description"
          />
        </ul>
        <div v-if="step.id === 6">
          <p>Does your business provide design services?</p>
          <ul>
            <BoxListItem
              v-for="item in buildingCoverageItems"
              :key="item.id"
              :icon="item.icon"
              :name="item.name"
              :description="item.description"
            />
          </ul>
        </div>
        <input v-else-if="step.id === 7" />
      </section>
    </li>
  </ul>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import BoxListItem from "./BoxListItem.vue";
import InputText from "./InputText.vue";
import ListItemBold from "./ListItemBold.vue";

export default defineComponent({
  name: "StartScreen",
  prop: {
    buttonHandler: Function,
    stepData: Object,
    currentStep: Number
  },
  components: {
    BoxListItem,
    ListItemBold,
    InputText
  },
  data() {
    return {
      steps: [
        {
          id: 1,
          text: "What type of insurance are you looking for?",
          value: ""
        },
        { id: 2, text: "What’s the name of your business?", value: "" },
        { id: 3, text: "What’s the phone number?", value: "" },
        { id: 4, text: "What state do you operate from?", value: "" },
        { id: 5, text: "Do you do your own design?", value: "" },
        { id: 6, text: "Include building coverage?", value: "" },
        { id: 7, text: "When did your business begin?", value: "" }
      ],
      insuranceItems: [
        {
          id: 1,
          name: "Professional Liability",
          description: "Erros & Omissions (E&O insurance)",
          icon: require("../assets/insurance-professional.svg")
        },
        {
          id: 2,
          name: "General Liability",
          description: "Help mitigate against loss (CGL insurance)",
          icon: require("../assets/insurance-general.svg")
        },
        {
          id: 3,
          name: "Business Owner’s Policy",
          description: "The complete package (BOP)",
          icon: require("../assets/insurance-business.svg")
        },
        {
          id: 4,
          name: "Cyber",
          description: "Internet-bsed risks (CLIC)",
          icon: require("../assets/insurance-cyber.svg")
        }
      ],
      designItems: [
        {
          id: 4,
          name: "Yes",
          description: "We do designs in-house",
          icon: require("../assets/design-yes.svg")
        },
        {
          id: 4,
          name: "No",
          description: "We’re gonna need some assistance",
          icon: require("../assets/design-no.svg")
        }
      ],
      buildingCoverageItems: [
        {
          id: 4,
          name: "Yes",
          description: "",
          icon: require("../assets/coverage-yes.svg")
        },
        {
          id: 4,
          name: "No",
          description: "",
          icon: require("../assets/coverage-no.svg")
        }
      ]
    };
  }
});
</script>

<style scoped>
ul {
  list-style-type: none;
  padding-left: 0;
  margin: 0;
  display: flex;
  flex-flow: column nowrap;
  align-items: center;
  justify-content: center;
}
.insurance-steps-list {
  margin-bottom: 3.75em;
}

section {
  margin-top: 2.5em;
  margin-bottom: 3.125em;
}
li[disabled="true"] p {
  opacity: 0.25;
}
li[disabled="true"] .list-icon {
  opacity: 0.25;
}
</style>
