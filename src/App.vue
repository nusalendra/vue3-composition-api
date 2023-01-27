<template>
  <UserComponent 
    :label="label" 
    :user="user"
    @submit="onSubmit"
  />

  <button @click="changeName">Change</button>
</template>

<script>
import {ref, reactive} from 'vue';
import UserComponent from './components/UserComponent.vue';

export default {
  components: { UserComponent },
  setup() {
    const label = ref('Biodata');

    const user = reactive({
      name: 'Nusalendra',
      age: 21
    });

    const changeName = () => {
      user.name = "Citra Resmi"
    };

    const onSubmit = (val) => {
      console.log(val);
    }

    return {
      label,
      user,
      changeName,
      onSubmit
    }
  }
}
</script>