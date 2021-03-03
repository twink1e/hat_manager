<template>
  <div id="app">
    <FileManager></FileManager>
    <DrawingBoard></DrawingBoard>
  </div>
</template>

<script>
import FileManager from "@/components/FileManager";
import DrawingBoard from "@/components/DrawingBoard";

export default {
  name: 'App',
  components: {
    DrawingBoard,
    FileManager
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
