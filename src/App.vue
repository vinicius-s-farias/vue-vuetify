<template>
  <v-app>
    <v-app-bar app color="#2196F3" dark>
        <v-app-bar-title> Testing</v-app-bar-title>
        <v-spacer></v-spacer>
          <v-btn
        v-for="(link, i) in links"
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
      

      <v-main>
        <v-content class="mx"> 
        <router-view></router-view>
        </v-content>
      </v-main>
   <v-footer
    color="primary lighten-1"
    padless
  >
    <v-row
      justify="center"
      no-gutters
    >
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
      <v-col
        class="primary lighten-2 py-4 text-center white--text"
        cols="12"
      >
        {{ new Date().getFullYear() }} — <strong>Vuetify</strong>
      </v-col>
    </v-row>
  </v-footer>
  </v-app>
</template>


<script>
export default {
  name: "App",

  components: {},

  data: () => ({
  links: [
    {
      label: "Home",
      path:   "/",
    },
    {
      label: "Projects",
      path: "/Projects",
    },
    {
      label: "Dashboard",
      path:   "/Dashboard"
    },
  ],

}),
  methods: {
    
  }
};
</script>