<template>
  <v-app id="inspire">
    <v-navigation-drawer v-model="drawer" app>
      <v-list-item>
        <v-list-item-content>
          <v-list-item-title class="text-h6">
            Vuetify ToDo
          </v-list-item-title>
          <v-list-item-subtitle>
            A todo-list for learning
          </v-list-item-subtitle>
        </v-list-item-content>
      </v-list-item>

      <v-divider></v-divider>

      <v-list dense nav>
        <v-list-item v-for="item in items" :key="item.title" :to="item.to" link>
          <v-list-item-icon>
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-item-icon>

          <v-list-item-content>
            <v-list-item-title>{{ item.title }}</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>

    <v-card class="overflow-hidden">
      <v-app-bar app color="secondary" dark shrink-on-scroll prominent src="https://picsum.photos/1920/1080?random"
        fade-img-on-scroll scroll-target="#scrolling-techniques-3">
        <template v-slot:img="{ props }">
          <v-img v-bind="props" gradient="to top right, rgba(100,115,201,.7), rgba(25,32,72,.7)"></v-img>
        </template>

        <v-app-bar-nav-icon @click="drawer = !drawer"></v-app-bar-nav-icon>

        <v-app-bar-title>Vuetify ToDo</v-app-bar-title>

        <!-- <v-spacer></v-spacer> -->

        <v-btn icon>
          <v-icon>mdi-magnify</v-icon>
        </v-btn>

        <v-btn icon>
          <v-icon>mdi-heart</v-icon>
        </v-btn>

        <v-btn icon>
          <v-icon>mdi-dots-vertical</v-icon>
        </v-btn>

        <template v-slot:extension>
          <v-tabs align-with-title>
            <v-tab @click="changeAlertState">Trigger Alert</v-tab>
          </v-tabs>
        </template>
      </v-app-bar>
    </v-card>
      <v-sheet id="scrolling-techniques-3" class="overflow-y-auto" max-height="900">
        <v-main>
          <router-view></router-view>
        </v-main>
        <v-container style="height: 1000px;">

      <v-alert
      :value="isAlertShown" 
      color="blue-grey"
      elevation="3"
      type="info"
      transition="fade-transition"
      >This is a test alert</v-alert>

        </v-container>
      </v-sheet>

  </v-app>
</template>

<script>
export default {
  data() {
    return {
      drawer: null,
      items: [
        { title: 'Todo', icon: 'mdi-format-list-checks', to: '/' },
        { title: 'About', icon: 'mdi-help-box', to: '/about' },
      ],
      isAlertShown: false
    }
  },
  methods: {
    changeAlertState() {
      this.isAlertShown = !this.isAlertShown
      console.log("isAlertShown:", this.isAlertShown)
    }
  }
}
</script>