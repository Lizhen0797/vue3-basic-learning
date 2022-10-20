<template>
  当前和为{{ sum }}
  <br />
  <button @click="sum++">x++</button>
  <br />
  {{ name }} {{ age }} {{ job.j1.salary }}
  <br />
  <button @click="name += '+'">name++</button>
  <button @click="age++">age++</button>
  <button @click="job.j1.salary++">salary++</button>
</template>

<script>
// import { h } from 'vue'
import { reactive, ref, shallowReadonly, toRefs } from 'vue'
export default {
  name: 'MyDemo',
  setup() {
    let sum = ref(0)

    let person = reactive({
      name: '李四',
      age: 24,
      job: {
        salary: '30k',
        j1: {
          salary: 20,
        },
      },
    })
    //
    //person = readonly(person)
    person = shallowReadonly(person)
    return {
      sum,
      ...toRefs(person),
    }
  },
}
</script>

<style></style>
