<template>
  <div class="editor" ref="container"></div>
</template>
<script setup lang="ts">
import { ref, onMounted, onUnmounted } from 'vue';
import { monaco } from './customMonaco';

const container = ref();

let editor: monaco.editor.IStandaloneCodeEditor;

const props = defineProps({
  content: String,
  language: String
})

onMounted(() => {
  editor = monaco.editor.create(container.value, {
    value: props.content,
    language: props.language,
    theme: 'vs-dark',
  });

  editor.onDidChangeModelContent(() => {
    console.log(editor.getValue())
  })
});

onUnmounted(() => {
  editor.dispose()
})

</script>
<style>
.editor {
  width: 100%;
  height: 200px;
}
</style>
