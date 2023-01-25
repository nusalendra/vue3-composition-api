<template>
  <div>Count : {{ nilai }}</div>
  <button @click="add">ADD</button>
</template>
 
<script>
import { reactive, ref, watch, toRefs } from "vue"

export default {
  setup() { 
    const counter = reactive({
      nilai: 0
    });

    const num1 = ref(1);
    const num2 = ref(2);

    const add = () => {
      num1.value++;
      num2.value++;

      counter.nilai++;
    };

    // --Akses 1 state menggunakan watch--
    watch(() => num1, (current, before) => {
      console.log(num1.value);
    })

    // Akses state reactive / object menggunakan watch
    watch(() => counter.nilai, (current, before) => {
      console.log(counter.nilai);
      console.log(current);
      console.log(before);
    })

    // Akses beberapa state sekaligus menggunakan watch
    watch([num1, num2], (current, before) => {
      console.log(num1.value);
      console.log(num2.value);
      console.log(current);
      console.log(before);
    })
    
    return {
      ...toRefs(counter),
      add,
    }
  }
}
</script>
