<template>
  <div id="app">
    <section>
      <h3>My Todo List</h3>
      <input type="text" v-model="state.todo" />
      <ul>
        <li v-for="(todo, i) in state.todolist" :key="i">
          {{todo}}
          <button @click="removeTodo(i)">x</button>
        </li>
      </ul>
    </section>
    <button @click="addTodo">Add Todo</button>
  </div>
</template>

<script>
import { reactive, ref } from "@vue/composition-api";
export default {
  setup() {
    const { state, addTodo, removeTodo } = useOurTodo();
    return {
      state,
      addTodo,
      removeTodo
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
  function removeTodo(i) {
    state.todolist.splice(i);
  }
  return {
    state,
    addTodo,
    removeTodo
  };
}
</script>

<style lang="sass">
</style>
