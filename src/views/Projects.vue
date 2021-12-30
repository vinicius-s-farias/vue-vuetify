
<template>
  <div class="Projects">
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

      <v-layout row class="mb-6">
        <v-tooltip top>
          <v-btn small flat color="white" @click="sortBy('title')" slot="activator">
          <v-icon left small>mdi-folder</v-icon>
          <span class="caption text-lowercase">By project name</span>
        </v-btn>
        <span>Sort projects by project name</span>
        </v-tooltip>

        <v-tooltip>
         <v-btn small flat color="grey" @click="sortBy('person')" slot="activator">
           <v-icon left small>mdi-comment-account</v-icon>
          <span class="caption text-lowercase">By person</span>
          </v-btn>
        </v-tooltip>
        <span></span>
      </v-layout>
      
      <v-card flat class="pa-3" v-for="project in projects" :key="project.title">
        <v-layout row wrap :class="`pa-3 project ${project.status}`">
          <v-flex xs12 md6>
            <div class="caption grey--text">Project Tittle </div>
              <div >{{project.title}}</div>
          </v-flex>
          <v-flex xs6 sm4 md2> 
            <div class="caption grey--text">Person</div>
            <div >{{project.person}}</div>
          </v-flex>
          <v-flex xs6 sm4 md2> 
            <div class="caption grey--text">Due by</div>
            <div >{{project.due}}</div>
          </v-flex>
          <v-flex xs6 sm4 md2> 
            <div class="caption grey--text">Aquele</div>
            <div >{{project.status}}</div>
          </v-flex>
        </v-layout>
        <v-divider></v-divider>
      </v-card>
       <v-btn>Normal</v-btn>
    <v-btn color="primary">
      Primary
    </v-btn>
    <v-btn color="error">
      Error
    </v-btn>
    <v-btn disabled>
      Disabled
    </v-btn>
 
    </v-countainer>

           <v-app-bar app dark>
      
      <v-app-bar-nav-icon @click="drawer = !drawer"></v-app-bar-nav-icon>
      
      <v-toolbar-title class="subheading green--text">Projects</v-toolbar-title>
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
    name: "App",

  data: () => ({
    
      projects: [

        { title: 'Design a new website', person: 'The Net Ninja', due: '1st Jan 2019', status: 'ongoing', content: 'Lorem ipsum dolor sit amet consectetur adipisicing elit. Sunt consequuntur eos eligendi illum minima adipisci deleniti, dicta mollitia enim explicabo fugiat quidem ducimus praesentium voluptates porro molestias non sequi animi!'},

        { title: 'Code up the homepage', person: 'Chun Li', due: '10th Jan 2019', status: 'complete', content: 'Lorem ipsum dolor sit amet consectetur adipisicing elit. Sunt consequuntur eos eligendi illum minima adipisci deleniti, dicta mollitia enim explicabo fugiat quidem ducimus praesentium voluptates porro molestias non sequi animi!'},

        { title: 'Design video thumbnails', person: 'Ryu', due: '20th Dec 2018', status: 'complete', content: 'Lorem ipsum dolor sit amet consectetur adipisicing elit. Sunt consequuntur eos eligendi illum minima adipisci deleniti, dicta mollitia enim explicabo fugiat quidem ducimus praesentium voluptates porro molestias non sequi animi!'},

        { title: 'Create a community forum', person: 'Gouken', due: '20th Oct 2018', status: 'overdue', content: 'Lorem ipsum dolor sit amet consectetur adipisicing elit. Sunt consequuntur eos eligendi illum minima adipisci deleniti, dicta mollitia enim explicabo fugiat quidem ducimus praesentium voluptates porro molestias non sequi animi!'},

      ],
     drawer: false,
        items: [
          { title: 'Dashboard', icon: 'mdi-view-dashboard' },
          { title: 'Team', icon: 'mdi-account-box' },
          { title: 'Projects', icon: 'mdi-gavel' },
        ],
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
  methods:{
    sortBy(prop){
      this.projects.sort((a,b) => a[prop] < b[prop] ? -1 : 1)
    }
  }
}
</script>

<style >

.project.complete{
  border-left: 4px solid #3cd1c2;
}
.project.ongoing{
  border-left: 4px solid orange;
}

.project.overdue{
  border-left: 4px solid tomato;
}
.project.status{
  border-left: 4px solid green;
}


</style>