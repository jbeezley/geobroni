<template>
  <v-app>
    <v-navigation-drawer style="margin-top: 64px"
      persistent
      :mini-variant="miniVariant"
      :clipped="clipped"
      v-model="drawer"
      fixed
    >
      <v-list>
        <v-list-tile
          value="true"
          v-for="(item, i) in items"
          :key="i"
        >
          <v-list-tile-action>
            <v-icon v-html="item.icon"></v-icon>
          </v-list-tile-action>
          <v-list-tile-content>
            <v-list-tile-title v-text="item.title"></v-list-tile-title>
          </v-list-tile-content>
        </v-list-tile>
      </v-list>
    </v-navigation-drawer>
    <v-toolbar
      app
      :clipped-left="clipped"
    >
      <!--v-toolbar-side-icon @click.stop="drawer = !drawer"></v-toolbar-side-icon-->
      <v-btn icon @click.stop="miniVariant = !miniVariant">
        <v-icon v-html="miniVariant ? 'chevron_right' : 'chevron_left'"></v-icon>
      </v-btn>
      <!--v-btn icon @click.stop="fixed = !fixed">
        <v-icon>remove</v-icon>
      </v-btn-->
      <v-toolbar-title v-text="title"></v-toolbar-title>
      <v-spacer></v-spacer>
      <!--v-btn icon @click.stop="rightDrawer = !rightDrawer">
        <v-icon>menu</v-icon>
      </v-btn-->
    </v-toolbar>
    <v-content>
      <v-container fluid fill-height>
        <v-layout>
          <router-view/>
        </v-layout>
      </v-container>
    </v-content>
    <!--v-navigation-drawer
      temporary
      :right="right"
      v-model="rightDrawer"
      fixed
      app
    >
      <v-list>
        <v-list-tile @click="right = !right">
          <v-list-tile-action>
            <v-icon>compare_arrows</v-icon>
          </v-list-tile-action>
          <v-list-tile-title>Switch drawer (click me)</v-list-tile-title>
        </v-list-tile>
      </v-list>
    </v-navigation-drawer-->
    <!--v-footer :fixed="fixed" app>
      <span>&copy; 2017</span>
    </v-footer-->
  </v-app>
</template>

<style>
html, body {
  overflow: hidden;
  height: 100vh;
}
</style>

<style scoped>
.application {
  height: 100vh;
}
main.content {
  height: calc(100vh - 64px);
}
</style>

<script>
export default {
  data () {
    return {
      clipped: true,
      drawer: true,
      fixed: false,
      items: [{
        icon: 'bubble_chart',
        title: 'Inspire'
      }],
      miniVariant: true,
      right: true,
      rightDrawer: false,
      title: 'Resonant Geo'
    };
  },
  name: 'App'
};
</script>
