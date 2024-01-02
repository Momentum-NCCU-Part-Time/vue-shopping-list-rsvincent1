<script setup>
import { onMounted, ref } from 'vue';
import { defineProps } from 'vue';
import ShoppingList from './ShoppingList.vue'
import ListForm from './ListForm.vue';


const props = defineProps({
    list: Object,
});
const emit = defineEmits(["newList"])
const url = 'http://localhost:3000/lists/';
const lists = ref([])

const displayList = () => {
  fetch(url, {
    method: "GET",
  })
    .then((res) => res.json())
    .then(
(data) => {

        lists.value = data;
       console.log(data)
      }
    );
};

onMounted(() => {
    displayList(); 
})

const deleteList = () => {
       fetch(url + props.list.id, {
         method: "DELETE",
       })
         .then((res) => res.json())
         .then(() =>{
            displayList();
         })
         emit("newList", newList)
            // lists.value = ''
         
};
   
</script>
<template>
    
  <button @click.prevent="deleteList(list.id), displayList"> Delete</button>
</template>