<template>
<div>
  <div class="container">
      <div class="col-md-6 offset-md-3">
      <h1 class="text-center mb-4">Todo 어플리케이션</h1>
      <input type="text" class="form-control" v-model="userInput" @keyup.enter="addNewTodo">

        <div class="list-group">
          <button class="list-group-item text-left" v-for="todo in todoList" v-bind:key="todo">
          {{ todo }}
          </button>
        </div>
      </div>
  </div>
</div>
</template>

<script>
import axios from 'axios';

export default {
  name: 'Test',
  data() {
    return {
      userInput: '',
      todoList: [],
    };
  },
  components: {
  },
  methods: {
    addNewTodo() {
      this.todoList.push(this.userInput);
      this.userInput = '';
    },
    getTest() {
      const path = 'http://localhost:5000/test';
      axios.get(path)
        .then((res) => {
          this.msg = res.data;
        })
        .catch((error) => {
          // eslint-disable-next-line
          console.error(error);
        });
    },
  },
  created() {
    this.getTest();
  },
};
</script>
