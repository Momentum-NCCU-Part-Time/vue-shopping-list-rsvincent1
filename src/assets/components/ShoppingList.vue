<script setup>
import {ref} from "vue";
import ItemForm from './ItemForm.vue'
import DeletList from './DeleteList.vue'

const addedItem = ref('');
let lists = ref([]);
const url = "http://localhost:3000/lists/"


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

<div class="shopping-list" >

<div v-for="list in lists" :key="list.id">
 <h2 class="listTitle"> {{ list.title }} </h2>
 
 <div v-for="item in list.items" :key="item.id">
 <span class="listItems"> {{ item.itemName }}</span>
 <input v-bind="addedItem" type ="checkbox"/>
</div>
 <span class="updateTime">{{ list.updatedAt }}</span>


  <ItemForm :list="list"/>
  <DeletList :list="list"/>

</div>
</div>

</template>  

<!-- <ShoppingItems/> -->
  <!-- <ItemForm v-bind="list" /> -->
   
  <!-- <button @click.prevent="deleteNote(list.id)">Delete</button>
  <button @click.prevent="editList(list.id)">Edit</button> -->
  <!-- <form class="added-item"  @submit.prevent="addItem">
    <label>
          Add Shopping List Items 
          <input v-model="addedItem" type="text" name="item-name"/>
    </label>
  
          <input type="submit" value="Add" />
          </form> -->
 <!-- <ShoppingItems :list="list" :addItem="addItem" /> -->