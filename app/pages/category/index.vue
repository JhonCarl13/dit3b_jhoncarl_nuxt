<template>
  <div>
  <v-card
    title="Category"
    rounded="50"
    
  >
    <template v-slot:text>
      <v-text-field
        v-model="search"
        label="Search"
        prepend-inner-icon="mdi-magnify"
        variant="outlined"
        hide-details
        single-line
      ></v-text-field>
    </template>

    <v-data-table
      :headers="headers"
      :items="category.data"
      :search="search"
    ></v-data-table>
  </v-card>
  </div>
</template>

<script setup>
  import { ref } from 'vue'

  const search = ref('')
  
  const { data: category} = await useFetch('http://localhost:1337/api/categories');

  const headers = [
  
    { key: 'category_name', title: 'Category' },
    { key: 'description', title: 'Description' },
    { key: 'date_created', title: 'Date Created' },

  ]

  
</script>


<style>

</style>