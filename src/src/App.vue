<script setup lang="ts">

import ButtonCounter from "./components/ButtonCounter.vue";
</script>

<template>
  <main>
      <h1>Here is a child component!</h1>
      <ButtonCounter title="Button Counter" initial-value="0" @click-event="console.log('Click')">
        Click
      </ButtonCounter>
      <component :is="ButtonCounter">
        Clickk
      </component>
  </main>
</template>

<style scoped>
main {
  color: black;
}
</style>
