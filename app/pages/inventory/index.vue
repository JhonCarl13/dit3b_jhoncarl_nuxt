<template>
  <v-card
    title="Inventory"
    flat
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

    <v-select
  clearable label="Select"
  :items="category.data"
  item-title="category_name"
  item-value="id"
  variant="outlined"
></v-select>

    <v-data-table
      :headers="headers"
      :items="inventory.data"
      :search="search"
    ></v-data-table>
  </v-card>
</template>
<script setup>
  import { ref } from 'vue'

  const search = ref('')
  const { data: inventory } = await useFetch('http://localhost:1337/api/inventories?populate=category');
  const headers = [
   
    { key: 'product_name', title: 'Product Name' },
    { key: 'product_description', title: 'Description' },
    { key: 'quantity', title: 'Quantity' },
    { key: 'condition', title: 'Condition' },
    { key: 'location', title: 'Location' },
    { key: 'acquisition_date', title: 'Aquisition Date' },
    { key: 'acquisition_cost', title: 'Aquisition Cost' },
    { key: 'total_cost', title: 'Total Cost' },
  ]

</script>