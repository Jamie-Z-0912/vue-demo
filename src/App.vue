<template>
  <div id="app">
    <div @click="toCopy" style="padding:10px; background: #aaa">我要复制</div>
    <img alt="Vue logo" src="./assets/logo.png" />
    <!-- <HelloWorld msg="Welcome to Your Vue.js App" /> -->
    <div :id="message">{{ message }}</div>
    <TodoList>
      <TodoItem
        :key="item.title"
        @showTitle="show"
        v-for="(item, index) in list"
        :del="item.del"
        :title="item.title"
      >
        <!-- vue 2.5 前写法 -->
        <!-- <span slot="pre-cion"></span> -->
        <!-- 作用域插槽 -->
        <!-- value 为子组件的值 -->
        <template v-slot:pre-icon="{ value }">
          <span v-if="value > 0.5" style="color:red">{{ value }}</span>
          <span v-else style="color:blue">{{ value }}</span>
        </template>
        <!-- 具名插槽 -->
        <template v-slot:suf-icon>
          <span>后置图标</span>
        </template>
        <button v-show="!item.del" slot="del-btn" @click="handleDelete(index)">
          删除
        </button>
      </TodoItem>
    </TodoList>
  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
import TodoList from "./components/TodoList";
import TodoItem from "./components/TodoItem";
import copy from "copy-to-clipboard";

export default {
  name: "App",
  components: {
    TodoList,
    TodoItem
  },
  data() {
    return {
      message: "Hello World",
      list: [
        {
          title: "课程1",
          del: false
        },
        {
          title: "课程2",
          del: false
        },
        {
          title: "课程3",
          del: false
        },
        {
          title: "课程4",
          del: false
        }
      ]
    };
  },
  methods: {
    handleDelete(val) {
      this.list[val].del = true;
    },
    show(val) {
      console.log("show", val);
      alert(val);
    },
    toCopy() {
      copy("复制文本") && alert(`复制成功`);
    }
  }
};
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
