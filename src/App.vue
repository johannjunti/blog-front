<script setup>
import { ref, computed } from 'vue';
import ItemList from './component/ItemList.vue';

let i = 0;
let message = ref('Helou Vue'); 
let items = ref([
  {id: i++, name:'Sai', isDone: true},
  {id: i++, name:'Muna', isDone: false},
  {id: i++, name:'Piim', isDone: true},
  {id: i++, name:'Või', isDone: false},
]);

function add(){
  if(message.value.trim() !== ''){
    items.value.push({id: i++, name:message.value.trim(), isDone: false});
  }
  message.value = '';
}

let doneItems = computed(() => {
  return items.value.filter(item => item.isDone)
});
let todoItems = computed(() => {
  return items.value.filter(item => !item.isDone)
});
</script>

<template>
<button @click="add">Click me</button>
<input type="text" v-model="message" @keydown.enter="add">

<ItemList :items="items" title="All Items"></ItemList>
<ItemList :items="doneItems" title="Done Items"></ItemList>
<ItemList :items="todoItems" title="Todo Items"></ItemList>

</template>
