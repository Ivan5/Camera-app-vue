<template>
  <div id="app">
    <Camera v-on:takePicture="this.takePicture"/>
  </div>
</template>

<script>
import Camera from "./components/Camera.vue";
export default {
  name: "app",
  components: { Camera },
  methods: {
    takePicture() {}
  }
};
</script>

<style lang="scss">
body {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  margin: 0;
  padding: 0;
  background-color: #f3f3f3;
}
</style>
