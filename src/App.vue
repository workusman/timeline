<template>
  <div id="app">
    <TimeLine />
  </div>
</template>

<script>
import TimeLine from "./components/TimeLine.vue";

export default {
  name: "App",
  components: {
    TimeLine,
  },
};
</script>

<style scoped>
#app {
  padding: 50px;
  max-width: 700px;
  margin: auto;
}
</style>