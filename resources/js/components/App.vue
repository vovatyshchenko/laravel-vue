<template>
  <v-app id="inspire">
    <v-navigation-drawer
      v-model="drawer"
      app
    >
      <v-list dense>
        <v-list-item link 
        v-for="(item, index) in nav_items"
        :key="index"
        :to="item.route"
        >
          <v-list-item-action>
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-item-action>
          <v-list-item-content>
            <v-list-item-title>{{ item.title }}</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>

    <v-app-bar
      app
      color="primary"
      dark
    >
      <v-app-bar-nav-icon @click.stop="drawer = !drawer" />
      <v-toolbar-title>ToDo LIST</v-toolbar-title>
      <v-spacer></v-spacer>
      <v-btn text v-for="(item, index) in nav_items"
      :key="index"
      :to="item.route"
       >
        <v-icon v-html="item.icon"></v-icon>{{ item.title }}
      </v-btn>
    </v-app-bar>

    <v-content>
      <v-container
        class="fill-height"
        fluid
      >
        <v-row
          align="center"
          justify="center"
        >
          <v-col class="text-center">
           <router-view></router-view>
          </v-col>
        </v-row>
      </v-container>
    </v-content>
    <v-footer
      color="primary"
      app
    >
      <span class="white--text">&copy; 2020</span>
    </v-footer>
  </v-app>
</template>

<script>
  export default {
    data: () => ({
      drawer: false,
    }),
    computed: {
      nav_items() {
        return [
          {
            icon: 'mdi-home',
            title: 'HOME',
            route: '/'
          },
          {
            icon: 'mdi-mail',
            title: 'ABOUT',
            route: '/about'
          }
        ];
      }
    },
  }
</script>