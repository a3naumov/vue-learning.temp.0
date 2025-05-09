<script setup lang="ts">

import {onMounted, useTemplateRef} from "vue";

const input = useTemplateRef('my-input')
onMounted(() => {
  input.value.focus()
})
</script>

<template>
  <main>
    <div>
      <input ref="my-input">
    </div>
  </main>
</template>

<style scoped>
main {
  color: black;
}
</style>
