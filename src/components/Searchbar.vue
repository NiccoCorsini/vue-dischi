<template>
  <div class="search">
    <form action="">
      <label for="search">Search artist or song:</label>
      <br />
      <input
        @keyup.enter="$emit('research', searchText)"
        @keyup.esc="
          $emit('reset', reset);
          resetSearchText();
        "
        type="text"
        name="search"
        v-model="searchText"
        placeholder="Search..."
      />
      <button @click.prevent="$emit('research', searchText)">
        search
      </button>
      <button
        @click.prevent="
          $emit('reset', reset);
          resetSearchText();
        "
      >
        reset
      </button>
    </form>

    <div class="select">
      <label for="select">Filter by genre:</label>
      <br />
      <select v-model="value" @change="$emit('options', value)" name="select">
        <option value="All">All</option>
        <option
          v-for="(genre, index) in genres"
          :key="genre + '-' + index"
          :value="genre"
          >{{ genre }}</option
        >
      </select>
    </div>
  </div>
</template>

<script>
export default {
  name: "Searchbar",
  props: {
    genres: Array,
  },
  data() {
    return {
      searchText: "",
      value: "All",
      reset: "",
    };
  },
  methods: {
    resetSearchText() {
      this.searchText = this.reset;
    },
  },
};
</script>

<style scoped lang="scss">
@import "../style/var";
@import "../style/functions";

.search {
  width: 100%;
  margin: 20px auto;
  display: flex;
  justify-content: center;
  flex-wrap: wrap;
  text-align: center;
  form {
    margin: 0 20px;
    filter: drop-shadow(0px 0px 6px rgba(0, 0, 0, 0.26));
  }
  label {
    color: $font-primary-color;
    padding-bottom: 15px;
    display: inline-block;
  }
  input {
    outline: none;
    border: none;
    border-top-left-radius: 20px;
    border-bottom-left-radius: 20px;
    padding: 10px;
    padding-left: 25px;
    background-color: rgb(224, 224, 224);
    transition: background-color 300ms;
    &:hover,
    &:focus {
      background-color: white;
    }
  }
  button {
    padding: 10px 15px;
    border: none;
    outline: none;
    text-transform: uppercase;
    font-weight: 500;
    background-color: #1ed760;
    color: $font-primary-color;
    cursor: pointer;
    &:last-child {
      padding-right: 20px;
      border-top-right-radius: 20px;
      border-bottom-right-radius: 20px;
      color: $font-secondary-color;
      background-color: $content-fill-color;
    }
    &:hover {
      @include hoverChooser(scale);
    }
  }
  .select {
    margin: 0 20px;
  }
}
</style>
