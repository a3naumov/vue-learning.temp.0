<script setup lang="ts">
import {ref} from "vue";

const count = ref(0)

const name = ref('Vue.js')
function greet(event) {
  alert(`Hello ${name.value}`)
  if (event) {
    alert(event.target.tagName)
  }
}

function say(message) {
  alert(message)
}
</script>

<template>
  <main>
    <div>
      <button @click="count++">Add 1</button>
      <p>Count is: {{ count }}</p>
    </div>

    <div>
      <button @click="greet">Greeting</button>
    </div>

    <div>
      <button @click="say('Hello')">Say hello</button>
      <button @click="say('Bye')">Say bye</button>
    </div>

    <div>
      <input @keyup.page-down="console.log(123)">
      <input @keyup.alt.enter="console.log(123)">
    </div>
  </main>
</template>

<style scoped>
main {
  color: black;
}
</style>
