<script>
import CardItem from "~/components/CardItem.vue";

export default {
  components: {
    CardItem
  },
  props: {
    title: {
      type: String,
      required: true,
      default: 'Todo List'
    },
    firstName: String,
    lastName: String,
    logger: Function,
    externalTask: Array,
  },
  emits: ['addTask', 'clickAdd'],
  name: 'TodoList',
  data() {
    return {
      tasks: [
        {
          title: 'title',
          description: 'desc',
          isDone: false,
        },
      ],
      searchQuery: '',
      searchQuery2: '',
      isCreating: false,
      titleValue: '',
      descriptionValue: '',
      customClass: '',
      type: 'C',
    }
  },
  methods: {
    addTask() {
      console.log('title: ', this.titleValue);
      console.log('description: ', this.descriptionValue);
      this.tasks.push({
        id: this.tasks.length + 1,
        title: this.titleValue,
        description: this.descriptionValue,
        isDone: false,
      })
      this.$emit('addTask', this.tasks);
    },
    handleCreate() {
      this.isCreating = !this.isCreating;
    },
    changeClass() {
      this.customClass = 'my-5';
    },
    resultQueryMethod() {
      console.log('run')
      if (this.searchQuery) {
        return this.tasks.filter((item) => {
          return this.searchQuery
              .toLowerCase()
              .split(" ")
              .every((v) => item.title.toLowerCase().includes(v));
        });
      } else {
        console.log(this.tasks);
        return this.tasks
      }
    },
    getData async function () {
      this.isLoading = true;
      await getFromApi();
      this.isLoading = false;
    }
  },
  computed: {
    resultQuery() {
      if (this.searchQuery) {
        return this.tasks.filter((item) => {
          return this.searchQuery
              .toLowerCase()
              .split(" ")
              .every((v) => item.title.toLowerCase().includes(v));
        });
      } else {
        return this.tasks
      }
    },
    display() {
      if (this.resultQuery.length > 0) {
        return true;
      } else {
        return false
      }
    }
  },
  mounted() {
    console.log(`At this point, vm.$el has been created and el has been
      replaced.`);
    console.log(this.$el.textContent) // Example component.
    this.searchQuery = 'title';
  },
  beforeUpdate() {
    console.log(`beforeUpdate: At this point, Virtual DOM has not re-rendered or patched yet.`)
// Logs the counter value every second, before the DOM updates.
    console.log(this.searchQuery)
  },
  updated() {
    console.log(`updated: At this point, Virtual DOM has re-rendered and patched.`)
// Fired every second, should always be true
    console.log(this.searchQuery)
  }
}

</script>
<template>
  <div class="list-task m-5">
    <h1>
      {{ `${title} ${firstName} ${lastName}` }}
    </h1>
    <input type="text" placeholder="search" v-model="searchQuery">
    <input type="text" placeholder="search" v-model="searchQuery2">
    <p v-if="display">Item dengan kata {{searchQuery}} ditemukan</p>
    <CardItem v-for="(item, i) of resultQuery" :task="item" :key="i" :isGrid="true"></CardItem>
    <div :class="`action py-2 ${customClass}`">
      <a
          href="#"
          class="add-button"
          v-if="!isCreating"
          @click="handleCreate"
      >
        Add Task
      </a>
      <div class="add-card" v-else>
        <div class="mb-2">
          <input v-model="titleValue" class="form-control mb-2" placeholder="Title" type="text">
          <textarea v-model="descriptionValue" class="form-control small" placeholder="Description"
                    rows="3"></textarea>
        </div>
        <div class="button-wrapper d-flex">
          <button class="btn btn-primary me-2" @click="addTask">Save</button>
          <button class="btn btn-outline-secondary" @click="isCreating = !isCreating">
            Cancel
          </button>
        </div>
      </div>
    </div>
  </div>
</template>
<style>
</style>
