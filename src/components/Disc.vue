<template>
  <div class="disk">
    <div class="img"><img :src="details.poster" :alt="details.title" /></div>
    <div class="details">
      <h3>{{ details.title }}</h3>
      <div>{{ details.author }}</div>
      <div>{{ details.year }}</div>
      <div>{{ details.genre }}</div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Disc",
  props: ["details"],
};
</script>

<style scoped lang="scss">
@import "../style/disc";
</style>
