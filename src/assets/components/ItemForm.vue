<script setup>
import { ref, defineProps } from 'vue'
import ShoppingItems from './ShoppingItems.vue'
import ShoppingList from './ShoppingList.vue'

const lists = ref([])
const addedItem = ref('')
const url = 'http://localhost:3000/shoppingList/'
const props = defineProps({ list: Object })
const emit = defineEmits(['NewAddedItem'])

// const displayList = () => {
//   fetch(url, {
//     method: 'GET'
//   })
//     .then((res) => res.json())
//     .then((data) => {
//       lists.value = data
//       console.log(data)
//     })
// }

const addItem = () => {
  fetch(url + props.list._id, {
    method: 'PATCH',
    headers: { 'Content-Type': 'application/json' },
    body: JSON.stringify({
      id: props.list.items.length + 1,
      title: props.list.title,
      items: [
        ...props.list.items,
        {
          id: props.list.items.length + 1,
          itemName: addedItem.value
        }
      ],

      updatedAt: new Date().toLocaleString().split(',')[0]
    })
  })
    .then((res) => res.json())
    .then((newItem) => {
      emit('NewAddedItem', newItem)
      addedItem.value = ''
    })
}

// displayList()
</script>

<template>
  <!-- <ShoppingList @newItem="displayList"/> -->
  <form class="add-shopping-item" @submit.prevent="addItem(); displayList()">
    <label>
      Add Shopping List Items
      <input v-model="addedItem" />
    </label>
    <input type="submit" value="Add" />
  </form>

  <ShoppingItems :list="props.list" />
</template>
