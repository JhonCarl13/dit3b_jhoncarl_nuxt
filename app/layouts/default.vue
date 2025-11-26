<template>
  <div>
    <v-app>
      <!-- Navigation -->
      <v-navigation-drawer
      v-model = "drawer"
       
      >
        <v-list>
          <v-list-item
            prepend-avatar="https://w7.pngwing.com/pngs/321/722/png-transparent-lion-vector-logo.png"
            subtitle="jhoncarl@gmailcom"
            title="Jhon Carl Del Rosario"
          ></v-list-item>
        </v-list>

        <v-divider></v-divider>

        <v-list density="compact" nav>
          <v-list-item to="/" prepend-icon="mdi mdi-view-dashboard-edit" title="Dashboard" value="myfiles"></v-list-item>
          <v-list-item to="/inventory" prepend-icon="mdi mdi-alarm-panel" title="Inventory" value="shared"></v-list-item>
          <v-list-item to="/category" prepend-icon="mdi mdi-shape-plus" title="Category" value="Users"></v-list-item>
          <v-list-item to="/users" prepend-icon="mdi mdi-account" title="Users" value="Users"></v-list-item>
        </v-list>
      </v-navigation-drawer>


      <!-- App Bar -->
      <v-app-bar :elevation="2">
  <template v-slot:prepend>
    <v-app-bar-nav-icon @click.stop="drawer =! drawer"></v-app-bar-nav-icon>
  </template>

  <v-app-bar-title>Application Bar</v-app-bar-title>
</v-app-bar>
      <v-main>
        <v-container>
          <slot />
        </v-container>
      </v-main>
    </v-app>
  </div>
</template>

<script setup>
const drawer= ref(true)
</script>
