<template>
  <header>
    <img src="../assets/img/logo.png" alt="spotify" />
  </header>
</template>

<script>
export default {
  name: "Header",
};
</script>

<style scoped lang="scss">
@import "../style/var";

header {
  background: $content-fill-color;
  margin-bottom: 20px;
  img {
    width: 50px;
    margin: 10px;
  }
}
</style>
