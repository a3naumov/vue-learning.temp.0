<script setup lang="ts">
import {ref, watch, watchEffect} from "vue";

const question = ref('')
const answer = ref('Questions usually contain a question mark. ;-)')
const loading = ref(false)
watch(question, async (newQuestion, oldQuestion) => {
  if (newQuestion.includes('?')) {
    loading.value = true
    answer.value = 'Thinking...'
    try {
      const res = await fetch('https://yesno.wtf/api')
      answer.value = (await res.json()).answer
    } catch (error) {
      answer.value = 'Error! Could not reach the API. ' + error
    } finally {
      loading.value = false
    }
  }
})



const x = ref(0)
const y = ref(0)
watch(x, (newX) => {
  console.log(`x is ${newX}`)
}, {once: true})
watch(
  () => x.value + y.value,
  (sum) => {
    console.log(`sum of x + y is: ${sum}`)
  }
)
watch(
  [x, () => y.value],
  ([newX, newY]) => {
    console.log(`x is ${newX} and y is ${newY}`)
  }
)
</script>

<template>
  <main>
    <div>
      <p>
        Ask a yes/no question:
        <input v-model="question" :disabled="loading">
      </p>
      <p>{{answer}}</p>
    </div>
    <div>
      <button @click="x++">X++</button>
      <button @click="x++;y++">X and y</button>
    </div>
  </main>
</template>

<style scoped>
main {
  color: black;
}
</style>
