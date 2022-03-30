<template>
  <div class="todo">
    <h1>Todo List</h1>
    <button v-if="editing" class="btn" @click="doEdit(false)">Cancel</button>
    <button v-else class="btn" @click="doEdit(true)">Add Item</button>
    <FormInput v-if="editing" @add-todo="addNewTodo($event)" />
    <button v-if="editing" class="btn remove" @click="removeAllTodos">
      Remove All Todos
    </button>
    <ul>
      <TodoItem
        v-for="(todo, index) in todos"
        :key="index"
        :todo="todo"
        @click="removeTodo(todo)"
      />
    </ul>
  </div>
</template>


<script setup>
import { ref } from "vue";
import TodoItem from "./components/TodoItem.vue";
import FormInput from "./components/FormInput.vue";

const todos = ref([]);
const editing = ref(false);

function addNewTodo(todo) {
  todos.value.push({
    id: Date.now(),
    done: false,
    content: todo,
  });
}

function removeTodo(todo) {
  todos.value = todos.value.filter((p) => p.id !== todo.id);
}
function removeAllTodos() {
  todos.value = [];
}

function doEdit(e) {
  editing.value = e;
  newItem.value = "";
}
</script>

<style>
#app {
  max-width: 1280px;
  margin: 0 auto;
}
.todo {
  display: flex;
  flex-direction: column;
  max-width: 700px;
  justify-content: center;
  text-align: center;
}
form {
  display: flex;
  flex-direction: column;
}

.action {
  cursor: pointer;
}

.post {
  padding: 15px;
  border: 1px solid teal;
  margin-top: 15px;
  display: flex;

  align-items: center;
  justify-content: space-between;
  border-radius: 5px;
}

.btn {
  margin-top: 15px;
  align-self: center;
  padding: 10px 15px;
  background: none;
  color: teal;
  border: 1px solid teal;
  border-radius: 5px;
  transition: all 0.3s;
}

.btn:active {
  box-shadow: 5px 5px 5px rgb(0, 183, 255);
  transform: scale(0.9);
}

.remove {
  display: flex;
  flex-direction: column;
  align-items: center;
  border-radius: 5px;
}
</style>