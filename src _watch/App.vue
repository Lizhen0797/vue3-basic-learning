<template>
  <h2>我是App组件</h2>
  {{ name }} {{ age }}
  <hr />
  {{ job.job }} {{ job.salary }} {{ job.test.test }}
  <button @click="name += '~'">changeName</button>
  <button @click="age += '~'">changeAge</button>
  <button @click="job.job += '~'">changeJob</button>
  <button @click="job.salary += 'k'">changeSalary</button>
  <button @click="job.test.test += 'k'">changeTestry</button>
</template>

<script>
// import { h } from 'vue'
import { ref, reactive, watch } from 'vue'
export default {
  name: 'App',
  components: {},
  setup() {
    const name = ref('张三')
    const age = ref(18)
    const job = reactive({
      job: '前端工程师',
      salary: '30k',
      test: {
        test: 1,
      },
    })

    // //监视ref定义的值
    // watch(name, (newValue, oldValue) => {
    //   console.log(newValue, oldValue)
    // })

    // //监视ref定义的多个值
    // //此处的newValue 和oldValue是监视多个值前后变化所产生的数组
    // watch([name, age], (newValue, oldValue) => {
    //   console.log(newValue, oldValue)
    // })

    // 监视reactive定义的对象 默认是开启deep的且将deep至于false也无法关闭deep: true
    // 注意：这里的newValue 和 oldValue一致无法获取
    // watch(job, (newValue, oldValue) => {
    //   console.log(newValue, oldValue)
    // })

    // // 监视reactive定义对象中某一个值
    // // 此处能够监视到oldValue
    // watch(
    //   () => job.job,
    //   (newValue, oldValue) => {
    //     console.log(newValue, oldValue)
    //   }
    // )

    // watch([job, name], (newValue, oldValue) => {
    //   console.log(newValue, oldValue)
    // })

    // watch([() => job.job, () => job.salary], (newValue, oldValue) => {
    //   console.log(newValue, oldValue)
    // })

    //最后一个特殊情况 此处无法监视到test.test: 1的改变
    // watch(
    //   () => job.test,
    //   (newValue, oldValue) => {
    //     console.log(newValue, oldValue)
    //   }
    // )
    // 此处可以监视到 job.test.test 的变化
    // 监视对象的某一个属性，如果该属性是一个对象，则deep: true有效且需要打开deep: true才能对起进行深度监视

    watch(
      () => job.test,
      (newValue, oldValue) => {
        console.log(newValue, oldValue)
      },
      {
        deep: true,
      }
    )
    return {
      name,
      age,
      job,
    }

    // 返回的渲染函数为主，页面中放什么已经不重要了
    // return () => {
    //   return h('h1', 'lizhen')
    // }
  },
}
</script>

<style></style>
