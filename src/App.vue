<template>
  <div>Count : {{ nilai }}</div>
  <button @click="add">ADD</button>

  <div>Result : {{ result }}</div>
</template>
 
<script>
import { reactive, ref, computed, toRefs } from "vue"

export default {
  setup() { 
    const counter = reactive({
      nilai: 0
    });

    const addNum = ref(1);

    const add = () => {
      addNum.value = 5;
      counter.nilai++;
    }

    const result = computed({
      get: () => counter.nilai + addNum.value,
      set: (val) => addNum = val
    })
    return {
      ...toRefs(counter),
      add,
      result
    }
  }
}
</script>
