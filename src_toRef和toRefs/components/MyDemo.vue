<template>
  {{ person.name }} {{ person.age }} {{ person.job.j1.salary }}
  {{ person }}
  <hr />
  {{ name }} {{ age }} {{ salary }}
  <hr />
  <button @click="name += '+'">name++</button>
  <button @click="age++">age++</button>
  <button @click="salary++">salary++</button>
</template>

<script>
// import { h } from 'vue'
import { reactive, toRef, toRefs } from 'vue'
export default {
  name: 'MyDemo',
  setup() {
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

    // const name = toRef(person, 'name')

    // watch(name, (newValue, oldValue) => {
    //   console.log(newValue, oldValue)
    // })

    // watch(person, (newValue, oldValue) => {
    //   console.log(newValue, oldValue)
    // })

    return {
      person,
      // name: toRef(person, 'name'),
      // age: toRef(person, 'age'),
      // salary: toRef(person.job.j1, 'salary'),
      ...toRefs(person),
      salary: toRef(person.job.j1, 'salary'),
    }
  },
}
</script>

<style></style>
