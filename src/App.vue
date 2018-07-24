<template>
  <v-app>
    <v-navigation-drawer
            :fixed="fixed"
            persistent
            :mini-variant="miniVariant"
            :clipped="clipped"
            v-model="drawer"
            enable-resize-watcher
            app
    >
      <v-list>
        <v-list-tile
                value="true"
                v-for="(item, i) in items"
                :key="i"
        >
          <router-link :to="item.path">
            <v-list-tile-action>
              <v-icon v-html="item.icon"></v-icon>
            </v-list-tile-action>
            <v-list-tile-content>
              <v-list-tile-title v-text="item.title"></v-list-tile-title>
            </v-list-tile-content>
          </router-link>

        </v-list-tile>
      </v-list>
    </v-navigation-drawer>
    <v-toolbar color="primary"
               :fixed="fixed"
               app
               :clipped-left="clipped"
    >
      <v-toolbar-side-icon @click.stop="drawer = !drawer" class="white--text hidden-md-and-up"></v-toolbar-side-icon>
      <v-toolbar-title class="white--text" v-text="title"></v-toolbar-title>
      <v-spacer></v-spacer>
      <span v-for="(item, i) in items"
            :key="i"
      >
        <v-btn class="white--text hidden-sm-and-down" flat @click="goTo(item.path)">{{item.title}}</v-btn>
      </span>
    </v-toolbar>
    <v-content>
      <router-view/>
    </v-content>
    <v-footer :fixed="fixed" app>
      <span>&copy; 2017</span>
    </v-footer>
  </v-app>
</template>

<script>

  export default {
    name: 'App',
    data() {
      return {
        clipped: false,
        drawer: false,
        fixed: true,
        items: [
          {
            path: '/',
            icon: 'home',
            title: 'Home'
          },
          {
            path: '/about',
            icon: 'info',
            title: 'About'
          },
          {
            path: '/contacts',
            icon: 'call',
            title: 'Contacts'
          }],
        miniVariant: false,
        right: true,
        rightDrawer: false,
        title: 'Carousel task'
      }
    },
    methods: {
      goTo(path) {
        this.$router.push({path})
      }
    }
  }
</script>

<style scoped>
  a {
    display: inline-flex;
    align-items: center;
    text-decoration: none;
  }
</style>

