<template>
  <Header />
  <Form @update="getTasks()"/>
  <div v-for="task in tasks" :key="task.id">
    <Card @remove="removeTask(task.id)" :task="task.title" />
  </div>
</template>

<script>
import Header from "./components/Header.vue";
import Form from "./components/Form.vue";
import Card from "./components/Card.vue";
import axios from 'axios'
export default {
  components: {
    Header,
    Form,
    Card
  },
  data() {
    return {
      tasks: []
    }
  },
  methods: {
   async getTasks() {
      let res = await axios.get('http://localhost:3000/tasks')
      this.tasks = res.data;
    },
    removeTask(id) {
      axios.delete(`http://localhost:3000/tasks/${id}`);
      this.tasks = this.tasks.filter((value) => value.id != id);
    }
  },
  mounted() {
    this.getTasks();
  },
}
</script>

<style scoped></style>
