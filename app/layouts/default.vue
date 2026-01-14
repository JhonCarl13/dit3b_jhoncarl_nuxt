<template>
  <v-app>

     <v-navigation-drawer
      v-model = "drawer"
      >
        <v-list>
          <v-list-item
            prepend-avatar="https://pbs.twimg.com/profile_images/1426180219061166081/ze9F3n7N_400x400.jpg"
            subtitle="DIT - 3B"
            title="Rafael Flores"
          ></v-list-item>
        </v-list>

        <v-divider></v-divider>

        <v-list density="compact" nav>
          <v-list-item to="dashboard" prepend-icon="mdi mdi-view-dashboard" title="Dashboard" value="myfiles"></v-list-item>
          <v-list-item to="/category" prepend-icon="mdi mdi-shape-plus" title="Category" value="shared"></v-list-item>
          <v-list-item to="/inventory" prepend-icon="mdi mdi-folder-account" title="Inventory" value="starred"></v-list-item>
          <v-list-item to="/user" prepend-icon="mdi mdi-folder-account" title="User" value="user"></v-list-item>
        </v-list>
      </v-navigation-drawer>

    <v-app-bar :elevation="3">
  <template v-slot:prepend>
    <v-app-bar-nav-icon @click.stop = "drawer =! drawer"></v-app-bar-nav-icon>
  </template>

  <v-app-bar-title>PixelCraft</v-app-bar-title>
</v-app-bar>


    <v-main>
      <v-container>
        <slot />
      </v-container>
    </v-main>
  </v-app>
</template>


<script setup >
const drawer = ref (true)
</script>