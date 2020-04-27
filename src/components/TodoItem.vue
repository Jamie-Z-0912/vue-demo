<template>
  <li>
    <slot name="pre-icon" :value="value"></slot>
    <span v-if="!del">{{ title }}</span>
    <span v-else style="text-decoration:line-through">{{ title }}</span>
    <!-- 默认 -->
    <slot name="suf-icon">😁</slot>
    <button @click="handleClick">展示</button>
    <slot name="del-btn"></slot>
    <span style=""></span>
  </li>
</template>

<script>
export default {
  props: {
    title: String,
    del: {
      type: Boolean,
      default: false
    }
  },
  data: function() {
    return {
      value: Math.random().toFixed(2)
    };
  },
  methods: {
    handleClick() {
      console.log("点击删除按钮");
      // 调用父级组件的方法，并传参
      this.$emit("showTitle", this.title);
    }
  }
};
</script>

<style>
</style>