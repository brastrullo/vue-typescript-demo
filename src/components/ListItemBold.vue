<template>
  <div>
    <span class="list-icon">
      <span class="list-icon-number">{{ n }}</span>
    </span>
    <p>{{ text }}</p>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: "IconListItem",
  props: {
    n: Number,
    text: String
  }
});
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
div {
  display: flex;
  flex-flow: row nowrap;
  align-items: center;
  justify-content: space-between;
  max-width: 19.5em;
}
div + div {
  margin-top: 1.438em;
}

.list-icon {
  border-radius: 50%;
  display: flex;
  flex-flow: row nowrap;
  min-width: 2.25em;
  min-height: 2.25em;
  margin-right: 1.313em;
  background: #a8daff;
}
.list-icon-number {
  margin: auto;
  font-family: Roboto;
  font-style: normal;
  font-weight: bold;
  font-size: 1.125em;
  color: #0074d9;
}
p {
  margin: 0;
  text-align: left;
  font-weight: bold;
  font-size: 1.5em;
}
</style>
