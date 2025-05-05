<script setup lang="ts">
const message: string = 'Hello World!'

const html = '<span style="color: red">This should be red.</span>'

let customId = 1
customId++

const objectOfAttrs = {
  id: 'container',
  class: 'wrapper',
  style: 'background-color:green',
}

const seen = true;

const event = 'click'
</script>

<template>
  <main>
    <h1>{{ message }}</h1>

    <div>
      <p>Using text interpolation: {{ html }}</p>
      <p>Using v-html directive <span v-html="html"></span></p>
    </div>

    <div v-bind:id="'custom-id-' + customId.toString()"></div>
    <div :id="'custom-short-hand-id-' + customId.toString()"></div>

    <div v-bind="objectOfAttrs"></div>

    <p v-if="seen">Now you see mee</p>

    <button v-on:click="console.log(1)"></button>
    <button @click="console.log(1)"></button>

    <button v-on:[event]="console.log(2)"></button>
    <button @[event]="console.log(2)"></button>

    <button v-on:submit.prevent="console.log(3)"></button>
    <button @click.once="console.log(3)"></button>
  </main>
</template>

<style scoped>
main {
  color: black;
}
</style>
