<template>
  <div id="app">
    <section>
      <input type="text" v-model="state.todo" />
      <ul>
        <li v-for="(todo, i) in state.todolist" :key="i">{{todo}}</li>
      </ul>
    </section>
    <button @click="addTodo">Add Todo</button>
  </div>
</template>

<script>
import { reactive, ref } from "@vue/composition-api";
export default {
  setup() {
    const { state, addTodo } = useOurTodo();
    return {
      state,
      addTodo
    };
  }
};

function useOurTodo() {
  let state = reactive({
    todo: "",
    todolist: []
  });

  function addTodo() {
    state.todolist.push(state.todo);
    state.todo = "";
  }
  return {
    state,
    addTodo
  };
}
</script>

<style lang="sass">
</style>
