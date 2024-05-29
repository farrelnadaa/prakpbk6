<!-- App.vue -->
<template>
  <div id="app">
    <EditableContent />
  </div>
</template>

<script>
import EditableContent from './components/EditableContent.vue';

export default {
  name: 'App',
  components: {
    EditableContent
  }
};
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
