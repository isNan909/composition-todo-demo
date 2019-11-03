<template>
  <div id="app">
    <section>
      <input type="text" v-model="todo" />
      <ul>
        <li v-for="(todo, i) in todolist" :key="i">{{todo}}</li>
      </ul>
    </section>
    <button @click="addTodo">Add Todo</button>
  </div>
</template>

<script>
export default {
  name: "app",
  data() {
    return {
      todo: "",
      todolist: []
    };
  },
  methods: {
    addTodo() {
      this.todolist.push(this.todo);
      this.todo = "";
    }
  }
};
</script>

<style lang="sass">

</style>
