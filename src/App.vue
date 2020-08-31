<template>
  <div id="app">
    <button @click="count++">inc count</button>
    <button @click="items.push(Math.round(100*Math.random()))">add items</button>
    <Child v-bind="{items, count}"/>
  </div>
</template>

<script>
import Child from "./Child.vue";

export default {
  name: "App",
  components: {
    Child
  },
  data() {
    return {
      count: 0,
      items: [1]
    };
  }
};
</script>
