<script setup>
import One from './one.vue'
import Two from './two.vue'
import Three from './three.vue'
import Four from './four.vue'

let key = $ref(0)
const interval = setInterval(() => {
  key++
}, 60 * 60 * 1000)
onUnmounted(() => {
  clearInterval(interval)
})
</script>

<template>
  <main :key="key" grid="~ cols-2 rows-2 text-2xl" h-screen>
    <One />
    <Two />
    <Three />
    <Four />
  </main>
</template>
