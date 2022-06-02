<template>
    <h1 class="text-3xl font-bold">{{ title }}</h1>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      title: "Twitch User Search",
    };
  },
};
</script>

<style>
#app {
  font-family: Inter, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  margin-top: 60px;
  color: rgb(232, 230, 227);
  background-color: rgb(14, 16, 23);
}
</style>
