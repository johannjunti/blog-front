<script setup>
import { ref } from 'vue';


let message = ref('Helou Vue'); 
let items = ref(['Sai', 'muna', 'piim', 'või'])
function add(){
  if(message.value.trim() !== ''){
    items.value.push(message.value.trim())
  }
  message.value = '';
}
</script>

<template>
<button @click="add">Click me</button>
<input type="text" v-model="message" @keydown.enter="add">
<ul>
  <li v-for="item in items">{{ item }}</li>
</ul>
</template>
