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
        <v-row justify="center">
          <v-col cols="8">
            <file-drop @input="logFiles"></file-drop>
          </v-col>
          <v-col cols="12" :key="file.name" v-for="(file, index) in fileList"
                 class="text-center"
          >{{index + 1}}: {{file.name}}</v-col>
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

  fileList: FileList | null = null

  /**
   * called from upload event
   */
  logFiles(fileList: FileList) {
      this.fileList = fileList;
  }

}
</script>
