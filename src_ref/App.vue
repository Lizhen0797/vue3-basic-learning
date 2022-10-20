<template>
  <h2>我是App组件</h2>
  {{ name }} {{ age }}
  <hr />
  {{ job.job }} {{ job.salary }}
  <button @click="changeInfo">changeInfo</button>
</template>

<script>
// import { h } from 'vue'
import { ref } from 'vue'
export default {
  name: 'App',
  components: {},
  setup() {
    const name = ref('张三')
    const age = ref(18)
    const job = ref({
      job: '前端工程师',
      salary: '30k',
    })

    function changeInfo() {
      console.log(job)
      name.value = '李四'
      age.value = 19
      job.value.job = '后端工程师'
      job.value.salary = '40k'
    }

    return {
      name,
      age,
      job,
      changeInfo,
    }

    // 返回的渲染函数为主，页面中放什么已经不重要了
    // return () => {
    //   return h('h1', 'lizhen')
    // }
  },
}
</script>

<style></style>
