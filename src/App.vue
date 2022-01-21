<template>
  <v-app id="inspire">
     <v-navigation-drawer
     v-model="drawer"
     app
     >
       
      <v-list-item>
        <v-list-item-content>
          <v-list-item-title class="text-h6">
            Menu
          </v-list-item-title>
          <v-list-item-subtitle>
            Vuetify Menu
          </v-list-item-subtitle>
        </v-list-item-content>
      </v-list-item>

      <v-divider></v-divider>

      <v-list
        dense
        nav
      >
        <v-list-item
          v-for="item in items"
          :key="item.title"
          :to="item.to"

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
    </v-navigation-drawer>

    <!-- Nav start -->
    <v-app-bar
      app
      color="#fcb69f"
      dark
      src="vintage-1.png"
      prominent
    >
      <template v-slot:img="{ props }">
        <v-img
          v-bind="props"
          
        ></v-img>
      </template>
      <!-- section que nos hara acceder al panel lateral -->
      <v-app-bar-nav-icon @click="drawer =!drawer"></v-app-bar-nav-icon>


      <v-spacer></v-spacer>

    
    </v-app-bar>
    <!-- Nav end -->

    <v-main>
      <router-view></router-view>
      <!--  -->
    </v-main>
  </v-app>
</template>

/* Para funcion de menu*/
<script>
 export default {
    data: () => ({ 
      drawer: null,
      items: [
          { title: 'To-do-List', icon: 'mdi-format-list-checks', to: '/' },
          { title: 'About', icon: 'mdi-information', to: '/about' },
        ],
     }),
  }
</script>

