<script setup lang="ts">
import { ref } from 'vue'
import axios from 'axios'
defineProps<{ msg: string }>()
const message = ref('')
const count = ref(0)
const list = ref([])
const add = () => {
  count.value++
}
const getList = async function () {
  const { data } = await axios.get("https://gorest.co.in/public/v2/todos");
  list.value = data;
}
</script>
<template>
  <h1 className="text-3xl font-bold underline text-red-500">
    Hello world!
  </h1>
  <h1>{{ msg +' '+ message }}</h1>
  <pre>{{ list }}</pre>
  <div class="card">
    <input type="text" class="bg-gray-200" v-model="message" />
    <button type="button" class="bg-red-500" @click="getList()">GET LIST</button>
    <button type="button" class="bg-green-500" @click="count++">count is {{ count }}</button>
    <p>
      Edit
      <code>components/HelloWorld.vue</code> to test HMR
    </p>
  </div>
  
  <p>
    Check out
    <a href="https://vuejs.org/guide/quick-start.html#local" target="_blank"
      >create-vue</a
    >, the official Vue + Vite starter
  </p>
  <p>
    Install
    <a href="https://github.com/vuejs/language-tools" target="_blank">Volar</a>
    in your IDE for a better DX
  </p>
  <p class="read-the-docs">Click on the Vite and Vue logos to learn more</p>
</template>

<style scoped>
.read-the-docs {
  color: #888;
}
</style>
