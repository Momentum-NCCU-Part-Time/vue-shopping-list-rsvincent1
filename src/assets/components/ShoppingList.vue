<script setup>
import {ref} from "vue";
// import ItemForm from './assets/components/ItemForm.vue';
import ItemForm from './ItemForm.vue'


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
 <span class="listTitle"> {{ list.title }} </span>
<div v-for="item in list.items" :key="item.id">
 <span class="listItems"> {{ item.itemName }}</span>

</div>
 <span class="updateTime">{{ list.updatedAt }}</span>
  <!-- <button @click.prevent="deleteNote(list.id)">Delete</button>
  <button @click.prevent="editList(list.id)">Edit</button> -->
  <ItemForm :list="list" />
</div>
</div>

</template>