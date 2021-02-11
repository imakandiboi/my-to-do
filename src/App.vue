<template>
  <div id="app" class="container">
    <h5>
      Welcome, <br />
      Any plans for <span><strong>TODAY</strong></span>
    </h5>
    <TodoHome msg="Kindly Make a list " />
    <TodoList />
  </div>
</template>

<script>
import TodoHome from "./components/TodoHome.vue";
import TodoList from "./components/TodoList.vue";

export default {
  name: "App",
  components: {
    TodoHome,
    TodoList,
  },
};
</script>

<style>
* {
  box-sizing: border-box;
}
.container {
  max-width: 600px;
  margin: 0 auto;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  border-radius: 5px;
  background-color: rgb(245, 216, 120);
}
</style>
