<script setup>
import { ref } from 'vue'
import { defineProps } from 'vue'
import ListForm from './ListForm.vue';

const props = defineProps({
  list: Object
})
const emit = defineEmits(['newList'])
const lists = ref([''])
const addedItem = ref('')

const url = 'http://localhost:3000/shoppingList/'

const index = props.list.items ;
// index.forEach((item) => console.log(item._id));
// console.log('HERE:', props.list.items._id)
// console.log('HERE:', props.list._id)
const deleteItem = () => {
const index = props.list.items ;

index.forEach((item) => {
  fetch(url + props.list._id + '/' + item._id, {
    method: 'DELETE'
  })

    .then((res) => res.json())
    .then((newList) => {
      
      emit('newList', newList)
    })
})
  // lists.value = ''
}

</script>

<template>
  
  <div v-for="item in list.items" :key="item._id">
    <button @click.prevent="deleteItem">X</button>
    <span class="listItems"> {{ item.itemName }}</span>
    <input v-bind="addedItem" type="checkbox" />
    

  </div>
</template>
