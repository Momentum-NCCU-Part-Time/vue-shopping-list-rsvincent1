<script setup>
import { ref } from 'vue';
import ListForm from './assets/components/ListForm.vue';
import ShoppingList from './assets/components/ShoppingList.vue';
import ItemForm from './assets/components/ItemForm.vue'

const props = defineProps([
  'ListTitle'
])



</script>

<template>
  <div>
    <h1>Vue Shopping List</h1>
    
    <!-- your code here -->
    <ListForm/>
<ItemForm/>
    <ShoppingList/>
  </div>
</template>

<style scoped>
</style>
