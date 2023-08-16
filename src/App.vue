<template>
  <HelloWorld />
  <TodoApp />
</template>

<script>
import HelloWorld from './components/HelloWorld.vue';
import TodoApp from "./components/TodoApp.vue";

export default {
  name: 'App',
  components: {
    HelloWorld,
    TodoApp
  }
}

</script>


