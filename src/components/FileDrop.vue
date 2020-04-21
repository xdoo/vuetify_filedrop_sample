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
      title="Click to grap a file from your PC!"
      color="indigo lighten-4"
      width="100%"
      style="cursor:pointer;border-style: solid;border-width: 4px;border-color: #303F9F;"
      height="200"
      class="pa-2"
    >
      <v-col 
        align-self="center"
        class="indigo--text text--darken-2">
        <v-row justify="center" align="end">
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
        <v-row justify="center">
          <span class="title">Drop your file here, or click for file selection dialog!</span>
        </v-row>
      </v-col>
    </v-sheet>
  </div>
</template>
<script lang="ts">
import Vue from "vue"
import { Component, Emit } from "vue-property-decorator"

@Component
export default class FileDrop extends Vue{
  
  // internal properties
  formUpload: boolean = false
  dragover: boolean = false
  
  mounted () {
    // to register listeners, we have to know the 
    // html elements
    const dropzone = document.getElementById("dropzone")
    const fileupload = document.getElementById("fileUpload")

    // register listeners on the file input
    if(fileupload) {
      fileupload.addEventListener("change", e => {
        const target = (e.target as HTMLInputElement)
        if(target.files) {
          this.filesSelected(target.files)
        }
      })
    }

    // register listeners on your dropzone / v-sheet
    if(dropzone) {
      // register all drag & drop event listeners
      dropzone.addEventListener("dragenter", e => {
        e.preventDefault()
        this.dragover = true
      })
      dropzone.addEventListener("dragleave", e => {
        e.preventDefault()
        this.dragover = false
      })
      dropzone.addEventListener("dragover", e => {
        e.preventDefault()
        this.dragover = true
      })
      dropzone.addEventListener("drop", e => {
        e.preventDefault()
        if(e.dataTransfer) {
          this.filesSelected(e.dataTransfer.files)
        }
      })

      // register event listener for keyboard usage
      dropzone.addEventListener("click", e => {
        e.preventDefault()
        if(fileupload) {
          fileupload.click()
        }
      })
      dropzone.addEventListener("keypress", e => {
        e.preventDefault()
        if (e.key === "Enter") {
          if(fileupload)
            fileupload.click()
        }
      })
    }
  }

  /**
   * upload event...
   */
  @Emit()
  filesSelected(fileList: FileList) {
    this.dragover = false
  }
}
</script>