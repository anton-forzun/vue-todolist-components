<template>
  <form @submit.prevent="addNewTodo()">
    <input class="input" v-model="newTodo" name="newTodo" />
    <button class="btn addBtn">Add new todo</button>
  </form>
</template>

<script setup>
import { defineEmits, ref } from "vue";
const newTodo = ref("");
const emit = defineEmits(["addTodo"]);

const addNewTodo = () => {
  emit("addTodo", newTodo.value);
  newTodo.value = "";
};
</script>

<style scoped>
.input {
  width: 100%;
  border: 1px solid teal;
  padding: 10px 15px;
  margin-top: 15px;
  color: teal;
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
.addBtn {
  border-radius: 5px;
}
.btn:active {
  box-shadow: 5px 5px 5px rgb(0, 183, 255);
  transform: scale(0.9);
}
</style>