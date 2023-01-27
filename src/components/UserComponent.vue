<template>
  <div>{{ label }} : {{ user.name }}</div>
  <div>{{ description }}</div>

  <button @click="submit">Submit</button>
</template>

<script>
import {toRefs, computed} from 'vue';
export default {
  props: {
    label: {
      type: String,
      default: ""
    },
    user: {
      type: Object,
      default: () => {}
    }
  },

  setup(props, { emit }) {
    const {label, user} = toRefs(props);

    const description = computed(() => {
      return `${label.value} : ${user.value.name}`;
    });

    const submit = () => {
      emit('submit', 'Ini adalah Submit');
    }
    return {
      description,
      submit
    }
  }
}
</script>