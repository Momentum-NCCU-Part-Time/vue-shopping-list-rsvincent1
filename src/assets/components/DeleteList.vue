<script setup>
import { ref } from 'vue';
import { defineProps } from 'vue';
import ShoppingList from './ShoppingList.vue'

const props = defineProps({
    list: Object,
});
const url = 'http://localhost:3000/lists/';



const deleteList = () => {
       fetch(url + props.list.id, {
         method: "DELETE",
       })
         .then((res) => res.json())

             displayList();
     
};

</script>
<template>
  <button @click.prevent="deleteList(list.id)"> Delete</button>

</template>