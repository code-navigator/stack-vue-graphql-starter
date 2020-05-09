<template>
  <v-app style="background: #E3E3EE">
    <!-- Side Navbar -->
    <v-navigation-drawer app temporary fixed v-model="sideNav">
      <v-toolbar color="accent" dark flat dense>
        <v-app-bar-nav-icon @click="toggleSideNav"></v-app-bar-nav-icon>
        <router-link to="/" tag="span" style="cursor: pointer">
          <h1 class="title pl-5">VueShare</h1>
        </router-link>
      </v-toolbar>

      <v-divider></v-divider>

      <!-- Side Navbar Links -->
      <v-list>
        <v-list-item-group>
          <v-list-item ripple v-for="item in sideNavItems" :key="item.title" :to="item.link">
            <v-list-item-icon>
              <v-icon v-text="item.icon"></v-icon>
            </v-list-item-icon>
            <v-list-item-content>
              {{ item.title }}
            </v-list-item-content>
          </v-list-item>
        </v-list-item-group>
      </v-list>
      </v-navigation-drawer>

    <!-- Horizontal Navbar -->
    <v-app-bar color="primary" app dark dense>

      <!-- App Title -->
      <v-app-bar-nav-icon @click="toggleSideNav"></v-app-bar-nav-icon>
      <v-toolbar-title class="hidden-xs-only">
        <router-link to="/" tag="span" style="cursor: pointer">
          VueShare
        </router-link>
      </v-toolbar-title>

      <v-spacer></v-spacer>

      <!-- Search Input -->
      <v-text-field flex prepend-inner-icon="mdi-magnify" placeholder="Search posts" color="primary" single-line hide-details></v-text-field>

      <v-spacer></v-spacer>

      <v-toolbar-items class="hidden-xs-only">
        <v-btn text v-for="item in horizontalNavItems" :key="item.title" :to="item.link">
          <v-icon class="hidden-sm-only">{{ item.icon }}</v-icon>
          {{ item.title }}
        </v-btn>
      </v-toolbar-items>

    </v-app-bar>

    <!-- App Content -->
    <main>
      <v-container class="mt-5">
        <transition name="fade">
          <router-view/>
        </transition>
      </v-container>
    </main>
  </v-app>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      sideNav: false
    }
  },
  computed: {
    horizontalNavItems() {
      return [
        {icon: 'mdi-message-text', title: 'Posts', link: '/posts'},
        {icon: 'mdi-lock-open', title: 'Sign In', link: '/signin'},
        {icon: 'mdi-pencil', title: 'Sign Up', link: '/signup'}
      ]
    },
    sideNavItems() {
      return [
        {icon: 'mdi-message-text', title: 'Posts', link: '/posts'},
        {icon: 'mdi-lock-open', title: 'Sign In', link: '/signin'},
        {icon: 'mdi-pencil', title: 'Sign Up', link: '/signup'}
      ]
    }
  },
  methods: {
    toggleSideNav() {
      this.sideNav = !this.sideNav
    }
  }
}
</script>

<style scoped>
  .fade-enter-active,
  .fade-leave-active {
    transition-property: opacity;
    transition-duration: 0.25s;
  }

  .fade-enter-active {
    transition-delay: .25s;
  }

  .fade-enter,
  .fade-leave-active {
    opacity: 0;

  }
</style>