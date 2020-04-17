<template>
  <v-app>
    <v-app-bar
      app
      color="black"
      dark
    >
      <span class="headline">FileDrop</span><span class="font-weight-light headline">Sample</span>

      <v-spacer></v-spacer>

      <v-icon title="blubbber...">mdi-flask-outline</v-icon>
    </v-app-bar>

    <v-content>
      <v-container fill-height>
        <v-row>
          <v-col cols="2"></v-col>
          <v-col cols="8">
            <file-drop v-on:files-selected="logFiles"></file-drop>
          </v-col>
          <v-col cols="2"></v-col>
        </v-row>
      </v-container>
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

  /**
   * called from upload event
   */
  logFiles(fileList: FileList) {
    for(const item of fileList) {
      // eslint-disable-next-line
      console.log(item.name)
    }
  }

}
</script>
