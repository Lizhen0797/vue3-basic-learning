<template>
  <h2>我是App组件</h2>
  {{ name }} {{ age }}
  <button @click="sayHello">sayHello</button>
</template>

<script>
// import { h } from 'vue'
export default {
  name: 'App',
  components: {},
  setup() {
    let name = '张三'
    let age = 18

    function sayHello() {
      alert(`我叫${name}, 今年${age}岁, 你好啊`)
    }

    return {
      name,
      age,
      sayHello,
    }

    // 返回的渲染函数为主，页面中放什么已经不重要了
    // return () => {
    //   return h('h1', 'lizhen')
    // }
  },
}
</script>

<style></style>
