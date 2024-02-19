<script setup>
import {ref} from "vue";
import ItemForm from './ItemForm.vue'
import DeletList from './DeleteList.vue'
import ListForm from './ListForm.vue';
import ShoppingItems from './ShoppingItems.vue';

import { defineProps } from 'vue'

const props = defineProps({
  list: Object
})

const addedItem = ref('');
let lists = ref([]);
const url = "http://localhost:3000/shoppingList/"


const displayList = () => {
  fetch(url, {
    method: "GET",
  })
    .then((res) => res.json())
    .then(
(data) => {

        lists.value = data;
       console.log(props.list)
  
      }
    );
};

displayList();


</script>
<template>

<ListForm @newList="displayList"/>

<div class="shopping-list" >

<div v-for="list in lists" :key="list._id">
 <h2 class="listTitle"> {{ list.title }} </h2>
 <div>
 

</div>



  <ItemForm :list="list"/>
  <DeletList :list="list"/>


</div>
</div>

</template>  

