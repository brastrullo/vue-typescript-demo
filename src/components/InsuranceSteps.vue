<template>
  <h1>{{ msg }}</h1>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: "StartScreen",
  props: {
    msg: String
  },
  data() {
    return {
      currentStep: 1,
      steps: [
        {
          id: 1,
          title: "What type of insurance are you looking for?",
          value: ""
        },
        { id: 2, title: "What’s the name of your business?", value: "" },
        { id: 3, title: "What’s the phone number?", value: "" },
        { id: 4, title: "What state do you operate from?", value: "" },
        { id: 5, title: "Do you do your own design?", value: "" },
        { id: 6, title: "Include building coverage?", value: "" },
        { id: 7, title: "When did your business begin?", value: "" }
      ]
    };
  }
});
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
