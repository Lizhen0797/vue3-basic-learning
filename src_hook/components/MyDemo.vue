<template>
  <h2>{{ sum }}</h2>
  <button @click="sum++">sum++</button>
  <hr />
  {{ point.x }} {{ point.y }}
</template>

<script>
import { ref } from 'vue'
import usePoint from '../hooks/usePoint'
export default {
  name: 'MyDemo',
  setup() {
    let sum = ref(0)
    let point = usePoint()
    return {
      sum,
      point,
    }
  },
}
</script>

<style lang="" scoped></style>
