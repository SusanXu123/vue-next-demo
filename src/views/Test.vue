<template>
  <div class="test">
    <h1>test count: {{count}}</h1>
    <div>count * 2 = {{doubleCount}}</div>
    <div>state from vuex {{a}}</div>
    <button @click="add">add</button>
    <button @click="update">update a</button>
  </div>
</template>

<script>
import { ref, computed, watch, getCurrentInstance } from 'vue'
export default {
  setup () {
    const count = ref(0)
    const add = () => {
      // 注意：需要用count.value++， 不是直接使用count++
      count.value++
    }
    const doubleCount = computed(() => count.value * 2)
    watch(() => count.value, (val, oldVal) => {
      console.log('watch--', val, oldVal)
    })
    const { ctx } = getCurrentInstance()
    console.log('route=', ctx.$router.currentRoute.value)
    const a = computed(() => ctx.$store.state.test.a)
    const update = () => {
      ctx.$store.commit('setTestA', count)
    }
    return {
      count,
      add,
      doubleCount,
      a,
      update
    }
  }
}
</script>
