<template>
  {{ x }}
  <button @click="x++">x</button>
  <hr />
  {{ person.name }} {{ person.age }} {{ person.job.j1.salary }}
  {{ person }}
  <hr />
  {{ name }} {{ age }} {{ job.j1.salary }}
  <hr />
  <button @click="name += '+'">name++</button>
  <button @click="age++">age++</button>
  <button @click="job.j1.salary++">salary++</button>
</template>

<script>
// import { h } from 'vue'
import { reactive, ref, toRefs } from 'vue'
export default {
  name: 'MyDemo',
  setup() {
    // shallowReactive 表示浅层的reactive 只考虑第一层数据的响应式
    // shallowRef不处理对象形式的数据 ref会将起转换为reactive响应式
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

    const x = ref(0)
    return {
      person,
      x,
      // name: toRef(person, 'name'),
      // age: toRef(person, 'age'),
      // salary: toRef(person.job.j1, 'salary'),
      ...toRefs(person),
    }
  },
}
</script>

<style></style>
