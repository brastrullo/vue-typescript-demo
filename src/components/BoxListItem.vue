<template>
  <li>
    <img :src="icon" :alt="`${name} Insurance Logo`" />
    <span>
      <p class="name">{{ name }}</p>
      <p class="description">{{ description }}</p>
    </span>
  </li>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: "Header",
  props: {
    name: String,
    description: String,
    icon: String
  }
});
</script>

<style scoped>
li {
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
li + li {
  margin-top: 1.25em;
}
img {
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
