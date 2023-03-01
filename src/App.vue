<template>
  <div id="app">
    <UserTable />
  </div>
</template>

<script>
import UserTable from "./components/UserTable/UserTable.vue";
export default {
  name: "App",
  components: { UserTable },
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
}
#app {
  max-width: 1160px;
  padding: 0 20px;
  margin: 0 auto;
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
</style>
