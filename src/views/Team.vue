<template>
  <div class="Team">
  <v-app id="inspire">
   <v-navigation-drawer
   v-model="drawer"
      app
      class="primary"
      dark
    
    >
      <v-list>
        <v-list-item
          v-for="item in items"
          :key="item.title"
          link
        >
          <v-list-item-icon>
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-item-icon>

          <v-list-item-content>
            <v-list-item-title>{{ item.title }}</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>

      <template v-slot:append>
        <div class="pa-2">
          
        </div>
      </template>
    </v-navigation-drawer>
    
     <v-countainer class="my-5">
      content
    </v-countainer>

           <v-app-bar app dark>
      
      <v-app-bar-nav-icon @click="drawer = !drawer"></v-app-bar-nav-icon>
      
      <v-toolbar-title>Team</v-toolbar-title>
      <v-spacer></v-spacer>
      <v-btn
        v-for="(link,i) in links"
        :key="i"
        color="white"
        text
        rounded
        class="my-2"
        :to="link.path"
      >
        {{ link.label }}
      </v-btn>
      </v-app-bar>

    </v-app>
  </div>
</template>
<script>
  export default {
    data: () => ({
    }),

  }