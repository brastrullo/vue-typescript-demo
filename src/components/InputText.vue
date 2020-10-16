<template>
  <input v-model="value" type="text" />
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: "InputText",
  props: {
    initialValue: String,
    validation: Function
  },
  data() {
    return {
      value: this.initialValue
    };
  },
  method: {
    validateInput() {
      console.log(this.value);
    }
  }
});
</script>

<style scoped>
input {
  background: none;
  border: none;
  border-bottom: 1px solid black;
  font-family: Roboto;
  font-size: 20px;
  line-height: 23px;
  color: #0074d9;
  padding-bottom: 7px;
  width: 100%;
}

input:focus {
  outline: none;
  border-bottom: 1px solid#0074d9;
}
</style>
