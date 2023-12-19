<!-- import ItemForm from "./assets/components/ListForm.vue" -->
<script>
import { ref } from "vue";
// import ShoppingList from './assets/components/ShoppingList.vue';


const url = "http://localhost:3000/lists";
const ListTitle = ref("")
let lists = ref([])
const saveList = () => {
  // const { title } = note;
  fetch(url, {
    method: "POST",
    headers: {
      "Content-Type": "application/json",
    },
    body: JSON.stringify({
      title: ListTitle.value,
      updatedAt: new Date()
    }),
  })
    .then((res) => res.json())
    

  lists.value.push({ title: ListTitle.value, updatedAt: new Date()});
  ListTitle.value = "";
  console.log("hey:", data)
  { 
    {
      
      lists.value;
    }
  }
};
// displayNote()
</script>
<ShoppingList/>
<template>

<form class="add-shopping-list" @submit.prevent="saveList" >
  
      
      <label>
        Shopping List Name 
        <input v-model="ListTitle" type="text" name="title" />
      </label>
      <!-- <label>
        Items
        <input v-model="ListItem" type="text" name="body" />
      </label> -->
      <input class="Add" type="submit" value="Add List" />
  

</form>

</template>