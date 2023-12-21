<script setup>
import { ref } from 'vue'
// import ShoppingList from './assets/components/ShoppingList.vue';

const listTitle = ref('')
const url = 'http://localhost:3000/lists/'
const saveList = () => {
  fetch(url, {
    method: 'POST',
    headers: { 'Content-Type': 'application/json' },
    body: JSON.stringify({ title: listTitle.value, items: [] })
  })
    .then((res) => res.json())
    .then((list) => {

      resetList(),
      displayList()
    })
}

const resetList = () => {
  listTitle.value = ''
}
</script>

<template>
  <form class="newList" @submit.prevent="saveList">
      <label>
        Shopping List Name 
        <input v-model="listTitle" type="text" name="title" />
      </label>
      <!-- <label>
        Items
        <input v-model="ListItem" type="text" name="body" />
      </label> -->
      <input class="Add" type="submit" value="Add List" />
  </form>
</template>


