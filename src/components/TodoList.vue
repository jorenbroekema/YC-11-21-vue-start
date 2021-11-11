<template>
  <h2>Hello {{ msg }}</h2>
  {{ todos }}
</template>

<script>
export default {
  props: ["msg"],
  data() {
    return {
      todos: [],
    };
  },
  mounted() {
    this.fetchTodos();
  },
  created() {
    this.addTodo();
  },
  methods: {
    async addTodo() {
      const body = { value: "pauze nemen" };
      await fetch("http://localhost:5000/todos", {
        method: "POST",
        headers: {
          "content-type": "application/json",
        },
        body: JSON.stringify(body),
      });
    },
    async fetchTodos() {
      const response = await fetch("http://localhost:5000/todos");
      const result = await response.json();
      this.todos = result;
    },
  },
};
</script>

<style scoped></style>
