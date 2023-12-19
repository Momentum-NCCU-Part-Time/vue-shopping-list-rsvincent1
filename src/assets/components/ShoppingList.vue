<script setup>
import {ref} from "vue";

// console.log()
// // const props = defineProps({
// //   title: ListTitle
// // })

// // const lists =[{
// //     "key": "id",
// //     "title": "ListTitle.value",

// // }]

// const newNote = ref("");
// const ListTitle = ref("");
// const ListBody = ref("");

let lists = ref([]);
const url = "http://localhost:3000/lists/"


const displayNote = () => {
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

displayNote();


</script>

<template>

<div class="shopping-list" >

<div v-for="list in lists" :key="list.id">
 <span class="listTitle"> {{ list.title }} </span>
<div v-for="item in list.items" :key="item.id">
 <span class="listItems"> {{ item.itemName }}</span>
</div>
 <span class="updateTime">{{ list.updatedAt }}</span>
  <button @click.prevent="deleteNote(list.id)">Delete</button>
  <button @click.prevent="editNote(list.id)">Edit</button>
</div>
</div>

</template>