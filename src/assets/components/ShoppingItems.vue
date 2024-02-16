<script setup>
import { ref } from 'vue'
import { defineProps } from 'vue';
// import ItemForm from './assets/components/ItemForm.vue'
import ItemForm from './ItemForm.vue'
// const props = defineProps(['list', 'addItem', ]);

const props = defineProps({
  list: Object
})
const emit = defineEmits(['newList'])
const lists = ref(['']);
const addedItem = ref('');

const url = 'http://localhost:3000/lists/itemId';

// const removeItem = () => {
//   fetch(url + props.list._id, {
//     method: 'PATCH',
//   })
//     .then((res) => res.json())
//     .then(() => {
//        console.log("HERE:", props.list.items)
//       // emit('newList', newList)
//       props.list = props.list.items.filter((items) => items.id !== props.list.id);
     
//     });
//   // item.itemName.value = addedItem.value.filter(i) => i !== 
// }
// removeItem()

const deleteItem = () => {
  fetch(url + props.list.items, {
    method: 'DELETE'
  })
    .then((res) => res.json())
    .then(() => {
      console.log("HERE:", props.list.items)
      // displayList()
    })
  emit('newList', newList)
  // lists.value = ''
}
// const displayList = () => {
//   fetch(url, {
//     method: "GET",
//   })
//     .then((res) => res.json())
//     .then(
// (data) => {

//         lists.value = data;
//        console.log(data)
//       }
//     );
// };

// const addItem = () =>{
//   fetch(url + props.list.id, {
//   method: 'PATCH',
//     headers: { 'Content-Type': 'application/json' },
//     body: JSON.stringify({
//       title: props.list.title,
//       items: props.list.items.push({
//          id: props.items.id,
//           itemName: addedItem.value,
//           purchased: 'false',
//         }),
//         updatedAt: new Date()
      
//     })
//   })
//     .then((res) => res.json())
//     .then((data) => {
      
//       addedItem.value = ''
//       console.log(addedItem)

//     })
//    addItem();
// }

// const resetItem = () => {
//   addedItem.value = ''
// }

</script>

<template>
    <!-- <button @click.prevent="deleteList(list.id)">Delete</button> -->
  <!-- <button @click="deleteItem"> X </button> -->
  <!-- <form> -->

<!-- <label>
          Add Shopping List Items 
          <input v-model="addedItem" @submit.prevent="addItem" type="text"/>
        </label>
        <input type="submit" value="Add" /> -->
        <!-- <ShoppingItems :item="items" :addItem="addItem"/>  -->
<!-- <div v-for="item in lists.items" :key="item.id">
     
     <span class="listItems"> {{ item.itemName }}</span>
</div> -->
<!-- </form> -->

    </template>