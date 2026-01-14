<template>
  <div>
  <v-card
    title="Inventory"
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

    <!-- Selectable Category -->
    <v-select
  v-model="selectedCategory"
  clearable
  label="Select Category"
  :items="category.data"
  item-title="category_name"
  item-value="id"
  variant="outlined"
></v-select>


    <v-data-table
      :headers="headers"
      :items="filteredInventory"
      :search="search"
    ></v-data-table>
  </v-card>
  </div>
</template>

<script setup>
  const search = ref("");
  const selectedCategory = ref(null);

  const { data: inventory} = await useFetch('http://localhost:1337/api/inventories?populate=category');

  const { data: category} = await useFetch('http://localhost:1337/api/categories');

  const headers = [
  
    { key: 'product_name', title: 'Inventory' },
    { key: 'product_description', title: 'Description' },
    { key: 'quantity', title: 'Quantity' },
    { key: 'unit', title: 'Unit' },
    { key: 'condition', title: 'Condition' },
    { key: 'location', title: 'Location' },
    { key: 'total_cost', title: 'Total Cost' },
    { key: 'remarks', title: 'Remarks' },
    { key: 'aquisition_cost', title: 'Cost' },
  ];
    const filteredInventory = computed(() => {
      if(!selectedCategory.value){
        return inventory.value.data;
      }else{
        return inventory.value.data.filter(item => item.category.id === selectedCategory.value); 
      }
    })
  
</script>


<style>

</style>