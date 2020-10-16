<template>
  <div class="container" v-for="item in items" :key="item.id">
    <input
      type="radio"
      class="input-radio"
      v-model="value"
      :id="`${step.name}${item.id}`"
      :name="step.name"
      :value="item.value"
      :step="step.id"
      @change.prevent="inputHandler, updateStep(step.id)"
    />
    <label :for="`${step.name}${item.id}`">
      <img :src="item.icon" :alt="`${item.name} Insurance Logo`" />
      <span>
        <p class="name">{{ item.name }}</p>
        <p class="description">{{ item.description }}</p>
      </span>
    </label>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: "InputRadio",
  props: {
    step: Object,
    initalValue: String,
    items: Array,
    inputHandler: Function,
    updateStep: Function
  },
  data() {
    return {
      value: this.initalValue
    };
  }
});
</script>

<style scoped>
.input-radio {
  position: absolute;
  width: 0;
  height: 0;
  display: none;
  visibility: hidden;
}
label {
  background: #ffffff;
  border: 1px solid #bdbdbd;
  box-sizing: border-box;
  box-shadow: 0px 4px 4px rgba(0, 0, 0, 0.1);
  border-radius: 4px;
  padding: 25px 20px;
  height: 5.5em;
  width: calc(100vw - (1.875em * 2));
  display: flex;
  flex-flow: row nowrap;
  align-items: center;
  position: relative;
}

.input-radio:checked + label {
  background: #ddf0ff;
}

.container + .container {
  margin-top: 1.25em;
}
label img {
  position: absolute;
}
span {
  margin-left: calc(1.875em + 1.25em);
  text-align: left;
}
.name {
  font-size: 1.064em;
  margin: 0;
}
.description {
  font-size: 0.75em;
  margin: 0;
}
</style>
