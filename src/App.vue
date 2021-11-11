<template>
  <h1>{{ title }}</h1>
  <form @submit="onSubmit">
    <label>
      Voornaam
      <input name="voornaam" type="text" />
    </label>
    <button>Submit</button>
  </form>
  <ol>
    <li v-for="item in list" v-bind:key="item.id">{{ item.value }}</li>
  </ol>
  <p v-if="bool">Only show this when bool is true</p>
  <p v-if="!bool">Only show this when bool is false</p>
  <HelloWorld msg="planet"></HelloWorld>
</template>

<style scoped>
h1 {
  color: orange;
}
</style>

<script>
import HelloWorld from "./components/HelloWorld.vue";

export default {
  components: {
    HelloWorld,
  },
  data() {
    return {
      bool: true,
      list: [
        { id: 1, value: "foo" },
        { id: 2, value: "bar" },
        { id: 3, value: "qux" },
      ],
      title: "Hello, World!",
    };
  },
  mounted() {
    setInterval(() => {
      this.bool = !this.bool;
    }, 1000);
  },
  methods: {
    onSubmit(ev) {
      ev.preventDefault();
      this.voornaam = ev.target.elements.voornaam.value;
    },
  },
};
</script>
