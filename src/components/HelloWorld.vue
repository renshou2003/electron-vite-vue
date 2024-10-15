<script setup lang="ts">
import { computed, onMounted, ref, inject } from 'vue'
import MyTest from './Mytest.vue'

defineProps<{ msg: string, id1?: string, id2?: string }>()

interface LOC {
  location: string,
  updateLocation: any
}

const location = inject<LOC>('location')

const count = ref(0)
const isBig = ref(false)
const mode = defineModel()

onMounted(() => {
  
  console.log('onmounted')
  console.log(location)
  mode.value = ['test1', 'test2', 'test3', 'test4']
})

function toggleBig(event: any) {
  isBig.value = !isBig.value
  if (event) {
    console.log(event.target.tagName)
  }
}

</script>

<template>
  <MyTest></MyTest>
  <h1>{{ `${msg}-${id1}-${id2}` }},{{ location?.location }}</h1>

  <div class="card">
    <button type="button" @click="count++">count is {{ count }}</button>
    <button type="button" @click="toggleBig">toggle</button>
    <h1 v-if="isBig">Vue is awesome!</h1>
    <h1 v-else>Oh no 😢</h1>
    <h1 v-show="!isBig">This use v-show!</h1>
    <p>
      Edit
      <code>components/HelloWorld.vue</code> to test HMR
    </p>
  </div>

  <p>
    Check out
    <a href="https://vuejs.org/guide/quick-start.html#local" target="_blank">create-vue</a>, the official Vue + Vite
    starter
  </p>
  <p>
    Install
    <a href="https://github.com/johnsoncodehk/volar" target="_blank">Volar</a>
    in your IDE for a better DX
  </p>
  <p class="read-the-docs">Click on the Vite and Vue logos to learn more</p>
</template>

<style scoped>
.read-the-docs {
  color: #888;
}
</style>
