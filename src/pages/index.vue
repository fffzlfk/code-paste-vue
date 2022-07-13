<script setup lang="ts">
import Codemirror from 'codemirror-editor-vue3'
// import 'codemirror/mode/javascript/javascript.js'
// import 'codemirror/theme/dracula.css'
const code = $ref('type to code...')

const cmOptions = {
  mode: 'text/javascript', // Language mode
  theme: 'dracula', // Theme
  lineNumbers: true, // Show line number
  smartIndent: true, // Smart indent
  indentUnit: 2, // The smart indent unit is 2 spaces in length
  foldGutter: true, // Code folding
  styleActiveLine: true, // Display the style of the selected row
}
</script>

<template>
  <Codemirror v-model:value="code" :options="cmOptions" border placeholder="test placeholder" :height="200" />
</template>
