<template>
  <v-app>
    <v-app-bar
      app
      elevation="4"
      color="primary"
      class="px-3"
    >
      <!-- Logo et titre -->
      <v-app-bar-nav-icon
        variant="text"
        @click.stop="drawer = !drawer"
        class="d-flex d-md-none"
      ></v-app-bar-nav-icon>
      
      <div class="d-flex align-center">
        <v-avatar size="40" color="rgba(255, 255, 255, 0.1)" class="mr-3">
          <v-icon color="white" size="24">mdi-star-shooting</v-icon>
        </v-avatar>
        <v-app-bar-title class="font-weight-bold">
          <span class="text-h5 conference-title">ConferencePro</span>
        </v-app-bar-title>
      </div>
      
      <v-spacer></v-spacer>

      <!-- Navigation pour écrans moyens et grands -->
      <div class="d-none d-md-flex">
        <v-btn variant="text" to="/" class="mx-1">
          <v-icon class="mr-1">mdi-home</v-icon>
          Home
        </v-btn>
        
        <v-btn variant="text" to="/dates" class="mx-1">
          <v-icon class="mr-1">mdi-calendar</v-icon>
          Important Dates
        </v-btn>
        
        <v-btn variant="text" to="/submission" class="mx-1">
          <v-icon class="mr-1">mdi-file-document-outline</v-icon>
          Submission
        </v-btn>
        
        <v-menu open-on-hover offset="10">
          <template v-slot:activator="{ props }">
            <v-btn variant="text" v-bind="props" class="mx-1">
              <v-icon class="mr-1">mdi-view-dashboard</v-icon>
              Program
              <v-icon end>mdi-chevron-down</v-icon>
            </v-btn>
          </template>
          <v-card min-width="220" elevation="8" rounded="lg" class="program-menu">
            <v-list density="compact">
              <v-list-item to="/program/chair" value="chair">
                <template v-slot:prepend>
                  <v-icon color="primary">mdi-account-tie</v-icon>
                </template>
                <v-list-item-title>Event Chair</v-list-item-title>
              </v-list-item>
              
              <v-list-item to="/program/committee" value="committee">
                <template v-slot:prepend>
                  <v-icon color="primary">mdi-account-group</v-icon>
                </template>
                <v-list-item-title>Scientific Committee</v-list-item-title>
              </v-list-item>
              
              <v-list-item to="/program/topics" value="topics">
                <template v-slot:prepend>
                  <v-icon color="primary">mdi-tag-multiple</v-icon>
                </template>
                <v-list-item-title>Topics</v-list-item-title>
              </v-list-item>
              
              <v-list-item to="/program/payment" value="payment">
                <template v-slot:prepend>
                  <v-icon color="primary">mdi-credit-card</v-icon>
                </template>
                <v-list-item-title>Payment Information</v-list-item-title>
              </v-list-item>
              
              <v-list-item to="/program/partners" value="partners">
                <template v-slot:prepend>
                  <v-icon color="primary">mdi-handshake</v-icon>
                </template>
                <v-list-item-title>Partners</v-list-item-title>
              </v-list-item>
            </v-list>
          </v-card>
        </v-menu>
        
        <v-btn variant="text" to="/speakers" class="mx-1">
          <v-icon class="mr-1">mdi-microphone</v-icon>
          Speakers
        </v-btn>
        
        <v-btn variant="text" to="/contact" class="mx-1">
          <v-icon class="mr-1">mdi-email</v-icon>
          Contact
        </v-btn>
      </div>
      
      <v-spacer></v-spacer>
      
      <v-btn
        variant="outlined"
        color="white"
        class="rounded-pill font-weight-bold"
        to="/register"
      >
        <v-icon class="mr-1">mdi-account-plus</v-icon>
        Register Now
      </v-btn>
    </v-app-bar>
    
    <!-- Drawer pour mobile -->
    <v-navigation-drawer
      v-model="drawer"
      temporary
      location="left"
    >
      <v-list>
        <v-list-item prepend-avatar="https://cdn.vuetifyjs.com/images/logos/vuetify-logo-dark.png">
          <v-list-item-title class="text-h6">ConferencePro</v-list-item-title>
          <v-list-item-subtitle>International Conference</v-list-item-subtitle>
        </v-list-item>
        
        <v-divider class="my-2"></v-divider>
        
        <v-list-item to="/" prepend-icon="mdi-home" title="Home"></v-list-item>
        <v-list-item to="/dates" prepend-icon="mdi-calendar" title="Important Dates"></v-list-item>
        <v-list-item to="/submission" prepend-icon="mdi-file-document-outline" title="Submission"></v-list-item>
        
        <v-list-group value="program">
          <template v-slot:activator="{ props }">
            <v-list-item
              v-bind="props"
              prepend-icon="mdi-view-dashboard"
              title="Program"
            ></v-list-item>
          </template>
          <v-list-item to="/program/chair" prepend-icon="mdi-account-tie" title="Event Chair"></v-list-item>
          <v-list-item to="/program/committee" prepend-icon="mdi-account-group" title="Scientific Committee"></v-list-item>
          <v-list-item to="/program/topics" prepend-icon="mdi-tag-multiple" title="Topics"></v-list-item>
          <v-list-item to="/program/payment" prepend-icon="mdi-credit-card" title="Payment Information"></v-list-item>
          <v-list-item to="/program/partners" prepend-icon="mdi-handshake" title="Partners"></v-list-item>
        </v-list-group>
        
        <v-list-item to="/speakers" prepend-icon="mdi-microphone" title="Speakers"></v-list-item>
        <v-list-item to="/contact" prepend-icon="mdi-email" title="Contact"></v-list-item>
        
        <v-divider class="my-2"></v-divider>
        
        <v-list-item to="/register" prepend-icon="mdi-account-plus" title="Register Now" color="primary"></v-list-item>
      </v-list>
    </v-navigation-drawer>
    
    <!-- Contenu principal -->
    <v-main>
      <v-container fluid>
        <!-- Contenu de la page -->
      </v-container>
    </v-main>
  </v-app>
</template>

<script setup>
import { ref } from 'vue';

const drawer = ref(false);
</script>

<style scoped>
.program-menu {
  overflow: hidden;
  border-radius: 8px;
}

.v-list-item:hover {
  background-color: rgba(var(--v-theme-primary), 0.1);
}

.v-app-bar {
  background: linear-gradient(90deg, var(--v-theme-primary) 0%, var(--v-theme-secondary) 100%);
}

.v-app-bar-title span {
  background: linear-gradient(45deg, #ffffff 30%, #e0e0e0 90%);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  text-shadow: 0 2px 4px rgba(0, 0, 0, 0.2);
}
</style>