<template>
  <div>
    <input 
      id="fileUpload"
      type="file" 
      accept="text/xml" 
      style="display:none"/>
    <v-sheet
      id="dropzone"
      tabindex="0"
      title="Klicken Sie hier, um eine Datei von Ihrem Rechner auszuwählen."
      color="indigo lighten-4"
      width="100%"
      style="cursor:pointer;border-style: solid;border-width: 4px;border-color: #303F9F;"
      height="200"
      class="pa-2"
    >
      <v-col class="indigo--text text--darken-2">
        <v-row justify="center" v-if="!loading">
          <v-icon
            v-if="!dragover" 
            color="indigo darken-2" 
            size="50"
            >mdi-cloud-upload-outline</v-icon>
          <v-icon
            v-if="dragover" 
            color="indigo darken-2" 
            size="50"
            >mdi-book-plus</v-icon>
        </v-row>
        <v-row justify="center" v-if="!loading">
          <span class="title">Drop your file here, or click for selection dialog!</span>
        </v-row>
        <v-row justify="center" v-if="loading">
          <v-progress-circular
            size="50"
            width="15"
            color="indigo darken-2"
            indeterminate
          ></v-progress-circular>
        </v-row>
        <v-row justify="center" v-if="loading">
          <span class="title">Datei wird verarbeitet</span>
        </v-row>
      </v-col>
    </v-sheet>
  </div>
</template>
<script lang="ts">
import Vue from "vue"
import { Component } from "vue-property-decorator"

@Component
export default class FileDrop extends Vue{
    
}
</script>