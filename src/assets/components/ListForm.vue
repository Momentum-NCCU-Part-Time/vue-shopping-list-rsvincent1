<script setup>
import { ref } from 'vue'

const emit = defineEmits(['newList'])

const resetList = () => {
  listTitle.value = ''
}

const listTitle = ref('')
const url = 'http://localhost:3000/shoppingList/'
const saveList = () => {
  fetch(url, {
    method: 'POST',
    headers: { 'Content-Type': 'application/json' },
    body: JSON.stringify({ title: listTitle.value, items: [] })
  })
    .then((res) => res.json())
    .then((newList) => {
      resetList()
      emit('newList', newList)
    })
}
</script>

<template>
  <form class="newList" @submit.prevent="saveList">
    <label>
      Shopping List Name
      <input v-model="listTitle" type="text" name="title" />
    </label>
    <input class="Add" type="submit" value="Add List" />
  </form>
</template>
