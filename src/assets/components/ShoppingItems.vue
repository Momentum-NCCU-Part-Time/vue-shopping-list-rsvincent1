<script setup>
import { ref } from 'vue'
import { defineProps } from 'vue';
// import ItemForm from './assets/components/ItemForm.vue'
import ItemForm from './ItemForm.vue'
// const props = defineProps(['list', 'addItem', ]);

const props = defineProps({
  items: Array, list: Object
})
const lists = ref(['']);
const addedItem = ref('');

const url = 'http://localhost:3000/lists/';

const removeItem = () => {
  fetch(url + props.list.id, {
    method: 'PATCH',
  })
    .then((res) => res.json())
    .then(() => {
       console.log("HERE:", props.list)
      // emit('newList', newList)
      props.list = props.list.filter((item) => item.id !== props.list.id);
     
    });
  // item.itemName.value = addedItem.value.filter(i) => i !== 
}
removeItem()
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