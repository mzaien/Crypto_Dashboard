<template>
  <v-app dark>
    <v-navigation-drawer
      v-model="drawer"
      :mini-variant="miniVariant"
      :clipped="clipped"
      fixed
      app
      permanent
      expand-on-hover
    >
      <v-list >
        <!-- <v-icon @click.stop="drawer = !drawer"  x-large >mdi-close-box</v-icon> -->
        <v-row class="ml-2 my-2">
       <router-link to="/">
        <v-img src="/logo.png" contain  max-height="40" max-width="40"/>
      </router-link>
      <!-- <v-toolbar-title v-text="title"  class="mx-4 font-weight-bold d-xs-none d-sm-none " /> -->
      </v-row>
        <v-list-item
          v-for="(item, i) in items"
          :key="i"
          :to="item.to"
          router
          exact
        >
          <v-list-item-action>
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-item-action>
          <v-list-item-content>
            <v-list-item-title v-text="item.title" />
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>
    <v-app-bar
      :clipped-left="clipped"
      fixed
      app
    >
    </v-app-bar>
    <v-main>
      <v-container>
        <nuxt keep-alive :keep-alive-props="{ max: 50 }"/>
      </v-container>
    </v-main>
    <v-footer
      :absolute="!fixed"
      app
    >
      <span>&copy; {{ new Date().getFullYear() }}</span>
    </v-footer>
  </v-app>
</template>

<script>
export default {
  data () {
    return {
      clipped: false,
      drawer: false,
      fixed: true,
      dialog: false,
      items: [
        {
          icon: 'mdi-calculator-variant',
          title: 'Exchange currencies',
          to: '/exchange'
        }
      ],
      miniVariant: false,
      right: true,
      rightDrawer: false,
      title: 'Crypto Dashboard',
    }
  }
}
</script>
