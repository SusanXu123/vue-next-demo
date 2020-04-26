<template>
  <div class="test">
    <h1>test count: {{count}}</h1>
    <button @click="add">add</button>
  </div>
</template>

<script>
import { ref } from 'vue'
export default {
  setup () {
    const count = ref(0)
    const add = () => {
      // 注意：需要用count.value++， 不是直接使用count++
      count.value++
    }
    return {
      count,
      add
    }
  }
}
</script>
