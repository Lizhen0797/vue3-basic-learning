<template>
  <h2>我是App组件</h2>
  {{ sum }} {{ msg }}
  <hr />
  {{ person.age }}
  <button @click="sum++">sum++</button>
  <button @click="msg += 'k'">msg++</button>
  <button @click="person.age++">sum++</button>
</template>

<script>
// import { h } from 'vue'
import { ref, reactive, watch, watchEffect } from 'vue'
export default {
  name: 'App',
  components: {},
  setup() {
    const msg = ref('张三')
    const sum = ref(18)
    const person = reactive({
      name: '李四',
      age: 24,
      job: {
        salary: '30k',
        j1: {
          salary: 20,
        },
      },
    })

    watchEffect(() => {
      const _x = sum.value
      const _y = person
      console.log('watchEffect', _x, _y)
    })

    watch(sum, (newValue, oldValue) => {
      console.log(newValue, oldValue)
    })
    return {
      msg,
      sum,
      person,
    }

    // 返回的渲染函数为主，页面中放什么已经不重要了
    // return () => {
    //   return h('h1', 'lizhen')
    // }
  },
}
</script>

<style></style>
