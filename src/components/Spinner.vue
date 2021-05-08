<template>
  <div class="spinner">
    <div>
      <span>Caricamento</span>
      <span>
        <slot></slot>
      </span>
    </div>
    <img :src="spinner" alt="spinner" />
    <div>in corso...</div>
  </div>
</template>

<script>
export default {
  name: "Spinner",
  data() {
    return {
      spinner: "http://pngimg.com/uploads/spinner/spinner_PNG44.png",
    };
  },
};
</script>

<style scoped lang="scss">
@import "../style/var";
@import "../style/functions";

.spinner {
  width: 100%;
  height: calc(100vh - 90px);
  color: $font-primary-color;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  img {
    width: 100px;
    margin: 2rem;
    @include rotate();
  }
}
</style>
