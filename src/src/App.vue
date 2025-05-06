<script setup lang="ts">
import {reactive, ref} from "vue";

const parentMessage = ref('Parent message');
const items = [
  {id:0, message: 'Foo'},
  {id: 1,message: 'Bar'},
]

const myObject = reactive({
  title: 'How to do lists in Vue',
  author: 'Jane Doe',
  publishedAt: '2016-04-10',
})
</script>

<template>
  <main>
    <div>
      <ul>
        <li v-for="item in items">
          {{item.message}}
        </li>
      </ul>
      <ul>
        <li v-for="(item, index) in items">
          {{ parentMessage}} - {{index}} - {{ item.message}}
        </li>
      </ul>
      <ul>
        <li v-for="({message}, index) in items">
          {{ message }} {{index}}
        </li>
      </ul>
    </div>

    <div>
      <ul>
        <li v-for="(value, key, index) in myObject">
          {{ index }}. {{ key }}: {{ value }}
        </li>
      </ul>
    </div>

    <div>
      <!-- 1-10 -->
      <span v-for="n in 10">{{n}}</span>
    </div>

    <div>
      <template v-for="item in items">
        <li>{{item.message}}</li>
        <li class="divider" role="presentation"></li>
      </template>
    </div>

    <div>
      <template v-for="item in items" :key="item.id">
        <li>{{item.message}}</li>
      </template>
    </div>
  </main>
</template>

<style scoped>
main {
  color: black;
}
</style>
