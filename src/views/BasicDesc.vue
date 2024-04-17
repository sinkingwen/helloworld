<template>
  <div id="demo">
    <li v-for="item in items">
      {{ item.message }}
    </li>
    <hr />
    <ul>
      <li v-for="value in myObject">
        {{ value }}
      </li>
    </ul>
    <hr />
    <li v-for="(value, key, index) in myObject" :key="index">
      {{ index }}. {{ key }}: {{ value }}
    </li>
  </div>
</template>

<script setup>
import { createApp, ref,reactive } from "vue";

const items = ref([{ message: "Foo" }, { message: "Bar" }]);
const myObject = reactive({
  title: "How to do lists in Vue",
  author: "Jane Doe",
  publishedAt: "2016-04-10",
});

createApp({
  data() {
    return {
      items,
    };
  },
}).mount("#demo");
</script>
