<script setup lang="ts">
import {ref} from "vue";

const message = ref('')

const checked = ref(false)

const checkedNames = ref([])

const picked = ref('')

const selected = ref('A')
const options = ref([
  { text: 'One', value: 'A' },
  { text: 'Two', value: 'B' },
  { text: 'Three', value: 'C' }
])

const toggle = ref(false)
const dynamicTrueValue = ref('yes1')
const dynamicFalseValue = ref('no2')
</script>

<template>
  <main>
    <div>
      <p>Message is: {{ message }}</p>
      <input v-model="message" placeholder="edit me" />
    </div>

    <div>
      <span>Multiline message is:</span>
      <p style="white-space: pre-line;">{{ message }}</p>
      <textarea v-model="message" placeholder="add multiple lines"></textarea>
    </div>

    <div>
      <input type="checkbox" id="checkbox" v-model="checked" />
      <label for="checkbox">{{ checked }}</label>
    </div>

    <div>
      <div>Checked names: {{ checkedNames }}</div>

      <input type="checkbox" id="jack" value="Jack" v-model="checkedNames" />
      <label for="jack">Jack</label>

      <input type="checkbox" id="john" value="John" v-model="checkedNames" />
      <label for="john">John</label>

      <input type="checkbox" id="mike" value="Mike" v-model="checkedNames" />
      <label for="mike">Mike</label>
    </div>

    <div>
      <div>Picked: {{ picked }}</div>

      <input type="radio" id="one" value="One" v-model="picked" />
      <label for="one">One</label>

      <input type="radio" id="two" value="Two" v-model="picked" />
      <label for="two">Two</label>
    </div>

    <div>
      <select v-model="selected">
        <option v-for="option in options" :value="option.value">
          {{ option.text }}
        </option>
      </select>

      <div>Selected: {{ selected }}</div>
    </div>

    <div>
      <input
        type="checkbox"
        v-model="toggle"
        :true-value="dynamicTrueValue"
        :false-value="dynamicFalseValue" />
      <p>{{toggle}}</p>
    </div>
  </main>
</template>

<style scoped>
main {
  color: black;
}
</style>
