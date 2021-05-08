<template>
  <div id="app">
    <Header />
    <Main />
  </div>
</template>

<script>
import Header from "./components/Header";
import Main from "./components/Main";

export default {
  name: "App",
  components: {
    Header,
    Main,
  },
};
</script>

<style lang="scss">
@import "https://cdnjs.cloudflare.com/ajax/libs/font-awesome/5.15.3/css/all.css";
@import "~@fontsource/roboto/index.css";
@import "~@fontsource/roboto/400.css";
@import "~@fontsource/roboto/500.css";
@import "~@fontsource/roboto/700.css";

@import "@/style/general";
</style>
