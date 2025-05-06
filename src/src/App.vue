<script setup lang="ts">
import {computed, reactive, ref} from "vue";

const isActive = false

const isActive1 = ref(true)
const hasError = ref(false)

const classObject = reactive({
  active: true,
  'text-danger': true,
})

const classObject1 = computed(() => ({
  active: isActive1.value,
  'has-error': hasError.value,
}))

const activeClass = ref('active')
const errorClass = ref('text-danger')

const activeColor = ref('red')
const fontSize = ref(30)
</script>

<template>
  <main>
    <div :class="{active: isActive}">isActive</div>

    <div
      class="static"
      :class="{ active: isActive1, 'text-danger': hasError }"
    >
      Binding to Objects
    </div>
    <div class="static" :class="classObject">Binding to Objects</div>
    <div class="static" :class="classObject1">Binding to Objects</div>

    <div :class="[activeClass, errorClass]">Binding to Arrays</div>
    <div :class="[isActive1 ? activeClass : '', errorClass]">Binding to Arrays</div>
    <div :class="[{ [activeClass]: isActive }, errorClass]">Binding to Arrays</div>

    <div :style="{color: activeColor, fontSize: fontSize + 'px'}">Binding Inline Styles</div>
    <div :style="{ display: ['-webkit-box', '-ms-flexbox', 'flex'] }">Multiple array values</div>
  </main>
</template>

<style scoped>
main {
  color: black;
}
</style>
