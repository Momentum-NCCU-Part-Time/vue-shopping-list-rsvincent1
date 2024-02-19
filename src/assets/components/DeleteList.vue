<script setup>
import { onMounted, ref } from 'vue'
import { defineProps } from 'vue'

const props = defineProps({
  list: Object
})
const emit = defineEmits(['newList'])
const url = 'http://localhost:3000/shoppingList/'
const lists = ref([])

const displayList = () => {
  fetch(url, {
    method: 'GET'
  })
    .then((res) => res.json())
    .then((data) => {
      lists.value = data
      console.log(data)
    })
}

onMounted(() => {
  displayList()
})

const deleteList = () => {
  fetch(url + props.list._id, {
    method: 'DELETE'
  })
    .then((res) => res.json())
    .then(() => {
      displayList()
    })
  emit('newList', newList)
  // lists.value = ''
}
</script>
<template>
    <div>
  <span class="updateTime">updated on: {{ list.updatedAt }}</span>
</div>
  <button @click.prevent="deleteList(list._id)">Delete</button>

</template>
