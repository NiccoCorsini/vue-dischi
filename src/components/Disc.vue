<template>
  <div class="disk">
    <div class="img"><img :src="details.poster" :alt="details.title" /></div>
    <h3>{{ details.title }}</h3>
    <div>{{ details.author }}</div>
    <div>{{ details.year }}</div>
    <div>{{ details.genre }}</div>
  </div>
</template>

<script>
export default {
  name: "Disc",
  props: ["details"],
};
</script>

<style scoped lang="scss">
@import "../style/var";
@import "../style/functions";

.disk {
  color: $font-primary-color;
  padding: 1rem;
  background: $content-fill-color;
  height: 380px;
  min-height: 380px;
  min-width: 120px;
  text-align: center;
  box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.123);
  @include hoverChooser(scale);
  .img {
    height: 50%;
    margin-bottom: 20px;
  }
  img {
    width: 100%;
    min-width: 100px;
  }
  h3 {
    text-transform: uppercase;
    font-size: 18px;
    margin-bottom: 15px;
  }
  div:not(:last-child) {
    color: $font-secondary-color;
    font-size: 15px;
  }
  div:last-child {
    margin-top: 10px;
    font-size: 13px;
    margin-bottom: 15px;
  }
}
</style>
