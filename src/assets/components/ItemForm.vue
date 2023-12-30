<script setup>

import{ref,defineProps} from 'vue';
// import ShoppingItems from './assets/components/ShoppingItems.vue'
//  import ShoppingItems from './assets/components/ShoppingItems.vue'
import ShoppingItems from './ShoppingItems.vue'
import ShoppingList from './ShoppingList.vue'

const lists = ref([])
const addedItem = ref('');
const url = 'http://localhost:3000/lists/';
const props = defineProps({ list: Object});
const emit = defineEmits(['NewAddedItem']);
// const Date = new Date();
// const props = defineProps(['list']);
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

const addItem = (list) =>{
  fetch(url + props.list.id, {
  method: 'PATCH',
    headers: { 'Content-Type': 'application/json' },
    body: JSON.stringify({
      id: props.list.items.length + 1,
      title: props.list.title,
      items: [
        ...props.list.items,
        {
          
          itemName: addedItem.value,
         
        },
      ],

      updatedAt: new Date().toISOString().split(',')[0]
    })
  })
    .then((res) => res.json())
    .then((newItem) => {
      emit('NewAddedItem', newItem)
       console.log()
      addedItem.value = ''
     
displayList()
    })

}


</script>

<template>
  <!-- class="add-Shoppingitem-form" v-for="item"> -->
  <!-- <div>
    
    <div v-for="item in lists.items" :key="item.id">
     
 <span class="listItems"> {{ item.itemName }}</span>

</div>
</div> -->
<form @submit.prevent="addItem">
        <label>
          Add Shopping List Items 
          <input v-model="addedItem"/>
        </label>
        <input type="submit" value="Add" />
    </form>  
    <!-- <ItemForm v-bind="list" /> --> 
   <!-- the bind line below will add the add button to  -->
        <!-- <ShoppingItems v-bind:addItem="addedItem"/> -->
        <!-- <ShoppingItems  :addItem="addItem"/>  -->
  </template>
  // @click.prevent="editList"

  
