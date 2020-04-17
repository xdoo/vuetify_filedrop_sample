<template>
  <v-app>
    <v-app-bar
      app
      color="black"
      dark
    >
      <span class="headline">FileDrop</span><span class="font-weight-light headline">Sample</span>

      <v-spacer></v-spacer>

      <v-btn
        href="https://github.com/vuetifyjs/vuetify/releases/latest"
        target="_blank"
        text
      >
        <span class="mr-2">Latest Release</span>
        <v-icon>mdi-open-in-new</v-icon>
      </v-btn>
    </v-app-bar>

    <v-content>
      <file-drop/>
    </v-content>
  </v-app>
</template>

<script lang="ts">
import Vue from "vue"
import { Component } from "vue-property-decorator"

// components
import FileDrop from "@/components/FileDrop.vue"

@Component({
  components: {
    FileDrop
  }
})
export default class App extends Vue {

}
</script>
