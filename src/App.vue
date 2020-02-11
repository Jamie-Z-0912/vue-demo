<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <!-- <HelloWorld msg="Welcome to Your Vue.js App" /> -->
    <div :id="message">{{message}}</div>
    <TodoList>
      <TodoItem :key="item.title" @delete="handleDelete" v-for="item in list" :del="item.del" :title="item.title">
        <template v-slot:pre-icon="{value}">
          <span>前置图标{{item.title}}{{value}}</span>
        </template>
      </TodoItem>
    </TodoList>
  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
import TodoList from './components/TodoList';
import TodoItem from './components/TodoItem';

export default {
  name: 'App',
  components: {
    TodoList,
    TodoItem,
  },
  data () {
    return {
      message: 'Hello World',
      list: [
        {
          title: '课程1',
          del: false,
        },
        {
          title: '课程2',
          del: false,
        },
      ]
    }
  },
  methods: {
    handleDelete (val) {
      console.log('handleDelete', val);
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
