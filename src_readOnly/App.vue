<template>
  <button @click="isShow = !isShow">更改显示</button>
  <hr />
  <MyDemo v-if="isShow"></MyDemo>
</template>

<script>
// import { h } from 'vue'
import { ref } from 'vue'
import MyDemo from './components/MyDemo'
export default {
  name: 'App',
  components: { MyDemo },
  setup() {
    let isShow = ref(true)
    return {
      isShow,
    }
  },
}
</script>

<style></style>
