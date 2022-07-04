<template>
  <div id="app" class="">
    <div id="nav">
      <router-link to="/all">全部</router-link> |
      <router-link to="/active">未完成</router-link> |
      <router-link to="/complete">已完成</router-link>
    </div>

    <div id="list" class="list-group">
      <TodoInput />
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

<style src="./assets/css/bootstrap.min.css"></style>
<style src="./assets/css/list-groups.css"></style>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  // -webkit-font-smoothing: antialiased;
  // -moz-osx-font-smoothing: grayscale;
  // text-align: center;
  color: #2c3e50;
  margin: 0 auto;
  height: 100vh;
}
#list {
  margin: 20px auto;
}
#nav {
  padding: 30px 0 0;
  text-align: center;

  a {
    font-weight: bold;
    color: #2c3e50;
  }
  a.router-link-exact-active {
    color: #42b983;
  }
}
.todoInput {
  margin: 0 0 10px;
}
</style>