<template>
  <h4>props:</h4>
  <span>{{ count }} - {{ items }}</span>
  <h4>composed computeds:</h4>
  <span>{{ countPlus1 }} - {{ itemsSorted }}</span>
  <p>
    'inc count' does not trigger the countPlus1 computed;
    why does 'add items' trigger the itemsSorted computed?
  </p>
</template>

<script>
import { ref, computed } from "vue";

export default {
  name: "Child",
  props: ["items", "count"],
  setup(props) {
    const count = ref(props.count); // does not work (expected)
    // const count = toRef(props, 'count') // works as expected

    const items = ref(props.items); // why does this work?
    // const items = toRef(props, 'items'); // shouldn't it be this?

    console.log('count', count, 'items', items)

    const itemsSorted = computed(() => [...items.value].sort());
    const countPlus1 = computed(() => count.value + 1);

    return { countPlus1, itemsSorted };
  }
};
</script>

<style>
h4 {
  margin-bottom: 0.5rem;
}
span {
  font-size: 1.5rem;
}
</style>