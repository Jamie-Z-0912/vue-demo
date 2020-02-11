<template>
  <li>
    <slot name="pre" :value="value"></slot>
    <span v-if="!del">{{title}}</span>
    <span v-else style="text-decoration:line-throw">{{title}}</span>
    <slot name="sub-icon">😄</slot>
    <button v-show="!del" @click="handleClick">删除</button>
  </li>
</template>

<script>
export default {
  props: {
    title: String,
    del: {
      type: Boolean,
      default: false,
    }
  },
  data: function () {
    return {
      value: Math.random()
    }
  },
  methods: {
    handleClick () {
      console.log('点击删除按钮');
      this.$emit('delete', this.title)
    }
  }
}
</script>

<style>
</style>