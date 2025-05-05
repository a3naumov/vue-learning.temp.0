<script setup lang="ts">
import {computed, reactive, ref} from 'vue'

const author = reactive({
  name: 'John Doe',
  books: ['Vue 2 - Advanced Guider', 'Vue 3 - Basic Guide', 'Vue 4 - The msytery'],
})

const publishedBooksMessage = computed(() => {
  return author.books.length > 0 ? 'Yes' : 'No'
})
console.log(publishedBooksMessage)



const firstName = ref('John')
const lastName = ref('Doe')

const fullName = computed({
  get() {
    return firstName.value + ' ' + lastName.value
  },
  set(newValue) {
    [firstName.value, lastName.value] = newValue.split(' ')
  }
})
fullName.value = 'John Doe'
console.log(firstName.value)
console.log(lastName.value)


const count = ref(2)
const alwaysSmall = computed((prevValue) => {
  console.log(prevValue)
  return count.value;
})
count.value++
console.log(alwaysSmall.value)
count.value++
console.log(alwaysSmall.value)
</script>

<template>
  <main>
    <div>
      <p>Has published books:</p>
      <span>{{ publishedBooksMessage }}</span>
    </div>
    <button @click="author.books = []"></button>
  </main>
</template>

<style scoped>
main {
  color: black;
}
</style>
