<template>
  <div id="app">
    <div id="nav">
      <router-link to="/all">全部</router-link> |
      <router-link to="/active">未完成</router-link> |
      <router-link to="/complete">已完成</router-link>
    </div>
    <TodoInput />
    <div id="list">
      <TodoListItem v-for="index in todoIndex" :key="index" :index="index" />
    </div>
  </div>
</template>

<script>
import TodoInput from "@/components/TodoInput/TodoInput.vue";
import TodoListItem from "@/components/TodoListItem/TodoListItem.vue";

export default {
  components: {
    TodoInput,
    TodoListItem,
  },
  mounted() {
    this.$store.dispatch("INIT_TODOS");
  },
  computed: {
    todoIndex() {
      return this.$store.getters["todoIndex"];
    },
  },
};
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  padding: 30px;
  a {
    font-weight: bold;
    color: #2c3e50;
  }
  a.router-link-exact-active {
    color: #42b983;
  }
}

body {
  background-color: bisque;
}
</style>