<script>
import{ref,defineProps} from "vue";
const addedItem = ref('');
const url = 'http://localhost:3000/lists/';
const props = defineProps({
  shoppingItem: Object, list: Object
})
 const addItem = () =>{
  fetch(url + props.list.id, {
  method: 'PATCH',
    headers: { 'Content-Type': 'application/json' },
    body: JSON.stringify({
      title: props.list.title,
      items: props.list.items.push({
        id: props.itemProp.id,
        itemName: addedItem.value,
        purchased: 'false'
      }),
      updatedAt: new Date()
    })
  })
    .then((res) => res.json())
    .then((item) => {
      console.log()
      /* emit("itemAdded", item) */
      resetItem()
    })
}

const resetItem = () => {
  addedItem.value = ''
}

</script>

<template>
  <!-- class="add-Shoppingitem-form" v-for="item"> -->
  <form >

  
        <label>
          Add Shopping List Items 
          <input v-model="addedItem" @click.prevent="addItem" type="text" name="body" />
        </label>
        <input type="submit" value="Add" />
    </form>  
  

  </template>
  // @click.prevent="editList"