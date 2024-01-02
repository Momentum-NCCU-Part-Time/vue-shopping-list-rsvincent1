<script setup>
import ShoppingList from './assets/components/ShoppingList.vue'

const props = defineProps(['ListTitle'])
</script>

<template>
  <div>
    <h1>Shopping List</h1>

    <ShoppingList />
  </div>
</template>

<style scoped></style>
