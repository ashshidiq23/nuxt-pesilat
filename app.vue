<script>
import 'bootstrap/dist/css/bootstrap.css'
import 'bootstrap-vue/dist/bootstrap-vue.css'
import TodoList from "~/components/TodoList.vue";
import Button from "~/components/Button.vue";
import Lifecycle from "~/components/Lifecycle.vue";
export default {
  components: {
    TodoList,
    Button,
    Lifecycle,
  },
  data() {
    return {
      firstName: 'John',
      lastName: 'Smith',
      signedUp: false,
      tasks: [
        {
          title: 'External Task 1',
          description: 'Description External Task 1'
        },
        {
          title: 'External Task 2',
          description: 'Description External Task 2'
        },
      ],
      showLifecycle: false,
    }
  },
  methods: {
    handleAddTask(value) {
      console.log(value);
    },
    handleClickAdd(value) {
      alert(value);
    }
  },
}
</script>

<template>
  <div>
    <TodoList
      title="Todo Task"
      :firstName="firstName"
      :lastName="lastName"
      @add-task="handleAddTask"
      @clickAdd="handleClickAdd"
    />
<!--    <Button className="p-5 mb-2"></Button>-->
<!--    <Computed />-->
    <button type="button" @click="showLifecycle = !showLifecycle">Toggle Lifecycle</button>
    <Lifecycle v-if="showLifecycle"/>
  </div>
</template>
