<template>
  <div class="hello">
    <h3>{{ msg }}</h3>
  </div>
</template>

<script>
export default {
  name: "TodoList",
  props: {
    msg: String,
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h5 {
  margin: 0px 0 0;
}
</style>
