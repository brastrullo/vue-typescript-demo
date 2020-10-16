<template>
  <input
    type="text"
    @change="
      e => {
        console.log(e.target.value);
      }
    "
  />
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: "InputText",
  props: {
    value: String
  }
});
</script>

<style scoped>
input {
  background: none;
  border: none;
  border-bottom: 1px solid black;
}
</style>
