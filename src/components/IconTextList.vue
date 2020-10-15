<template>
  <ul>
    <li v-for="item in list" :key="item.id" :n="item.id" :msg="item.msg">
      <i class="list-icon">
        <span>{{ item.id }}</span>
      </i>
      <p>{{ item.msg }}</p>
    </li>
  </ul>
</template>

<script lang="ts">
import { defineComponent } from "vue";

// const ListItem = {
//   name: "IconListItem",
//   props: {
//     n: Number,
//     msg: String
//   },
//   template: `<div>
//     <i class="list-icon">
//       <span>{{ n }}</span>
//     </i>
//     <p>{{ msg }}</p>
//   </div>
//   `
// };

export default defineComponent({
  name: "IconListItem",
  data() {
    return {
      list: [
        { id: 1, msg: "Answer a few simple questions about your business" },
        { id: 2, msg: "Browse through specially curated quotes" },
        {
          id: 3,
          msg: "Select your quote-of-choice and receive your policy instantly"
        }
      ]
    };
  },
  components: {
    // ListItem
  }
});
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
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
li {
  display: flex;
  flex-flow: row nowrap;
  align-items: center;
  justify-content: space-between;
  max-width: 19.5em;
}
li + li {
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
span {
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
}
</style>
