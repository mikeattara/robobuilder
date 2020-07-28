<template>
  <div id="app">
    <main>
      <RobotBuilder />
    </main>
  </div>
</template>

<script>
// import HomePage from "./home/HomePage.vue";
import RobotBuilder from './build/RobotBuilder.vue';

export default {
  name: 'App',
  components: {
    RobotBuilder,
  },
};
</script>

<style>
body {
  background: linear-gradient(to bottom, #555, #999);
  background-attachment: fixed;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
}
main {
  margin: 0 auto;
  padding: 30px;
  width: 1024px;
  background-color: white;
  min-height: 300px;
}
</style>
