<script setup lang="ts">
import {ref} from "vue";

const props = defineProps(['title', 'initialValue'])
const emit = defineEmits(['click-event'])

const counter = ref(props.initialValue ?? 5)

const increase = () => {
  counter.value++
  emit('click-event')
}
</script>

<template>
  <h2>{{title}}</h2>
  <p>{{counter}}</p>
  <button @click="increase"><slot /></button>
</template>
