<template>
  <div>
    <user-profile />
  </div>
</template>

<script>
import UserProfile from "@/components/UserProfile.vue";
export default {
  name: "App",
  components: {
    UserProfile,
  },
};
</script>

<style>
html, body {
  margin: 0px !important;
  padding: 0px !important;
}
#app {
  font-family: Arial, Helvetica, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  min-height: 100vh;
  background-color: #f3f5fa;
}
</style>