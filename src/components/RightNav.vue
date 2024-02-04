<template>
    <v-card>
      <v-layout>
        <v-navigation-drawer
          permanent
          location="right"
        >
          <template v-slot:prepend>
            <v-list-item
              lines="two"
              prepend-avatar="https://randomuser.me/api/portraits/women/82.jpg"
              title="Jane Smith"
              subtitle="Logged in"
            ></v-list-item>
          </template>
  
          <v-divider></v-divider>
  
          <v-list density="compact" nav>
            <router-link to="/">Home</router-link> |
            <router-link to="/about">About</router-link> |
            <router-link to="/friends">Friends</router-link>
            <!-- <v-list-item prepend-icon="mdi-home-city" title="Home" value="home" link to = "/"></v-list-item> -->
            <!-- <v-list-item prepend-icon="mdi-account" title="About" value="account" link to = "about"></v-list-item> -->
            <!-- <v-list-item prepend-icon="mdi-account-group-outline" title="Users" value="users" link to = "friends"></v-list-item> -->
          </v-list>
        </v-navigation-drawer>
        <!-- <v-main style="height: 250px">
        <v-col cols="auto">
      <v-card
        class="mx-auto"
        max-width="344"
        title="Avatars"
        subtitle="prepend-avatar and append-avatar"
        prepend-avatar="https://cdn.vuetifyjs.com/images/logos/v-alt.svg"
        append-avatar="https://cdn.vuetifyjs.com/images/john.jpg"
      >
        <v-card-text>Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod.</v-card-text>
      </v-card>
    </v-col>
</v-main> -->
      </v-layout>
    </v-card>
  </template>