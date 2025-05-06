<script setup lang="ts">
import {ref} from "vue";

const awesome = ref(true)

const type = 'C'
</script>

<template>
  <main>
    <div>
      <button @click="awesome = !awesome"></button>

      <h1 v-if="awesome">Vue is awesome</h1>
      <h1 v-else>Oh no</h1>
    </div>

    <div>
      <div v-if="type === 'A'">
        A
      </div>
      <div v-else-if="type === 'B'">
        B
      </div>
      <div v-else-if="type === 'C'">
        C
      </div>
      <div v-else>
        Not A/B/C
      </div>
    </div>

    <div>
      <template v-if="true">
        <h1>Title</h1>
        <p>Paragraph 1</p>
        <p>Paragraph 2</p>
      </template>
    </div>

    <div>
      <h1 v-show="false">Hello</h1>
    </div>
  </main>
</template>

<style scoped>
main {
  color: black;
}
</style>
