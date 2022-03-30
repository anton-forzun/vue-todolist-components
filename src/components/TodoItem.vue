<template>
  <li class="action post">
    <h3>{{ todo.content }}</h3>
    <button class="btn">remove todo</button>
  </li>
</template>

<script >
export default {
  props: {
    todo: {
      type: Object,
      required: true,
    },
  },
};
</script>

<style scoped>
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
</style>