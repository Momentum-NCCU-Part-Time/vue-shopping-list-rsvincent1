<script setup>
import {ref} from "vue";
import ItemForm from './ItemForm.vue'
import DeletList from './DeleteList.vue'
import ListForm from './ListForm.vue';
import ShoppingItems from './ShoppingItems.vue';

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
       console.log(data)
      }
    );
};

displayList();

</script>
<template>
 <!-- <ItemForm @NewAddedItem="displayList"/> -->
<ListForm @newList="displayList"/>
<!-- <ShoppingItems /> -->
<!-- <DeletList @newList="displayList"/> -->
<div class="shopping-list" >

<div v-for="list in lists" :key="list._id">
 <h2 class="listTitle"> {{ list.title }} </h2>
 
 <div v-for="item in list.items" :key="item.id">
  <button @click="deleteItem"> X </button>
  
 <span class="listItems"> {{ item.itemName }}</span>
 <input v-bind="addedItem" type ="checkbox"/>

</div>

 <span class="updateTime">updated on: {{ list.updatedAt }}</span>

  <ItemForm :list="list"/>
  <DeletList :list="list"/>

</div>
</div>

</template>  

