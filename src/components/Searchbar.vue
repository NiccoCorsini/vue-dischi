<template>
  <div class="search">
    <form action="">
      <label for="search">Search artist or album:</label>
      <br />
      <input
        @keyup.enter="$emit('research', searchText)"
        @keyup.esc="
          $emit('reset', reset);
          resetSearchText();
          resetSelect();
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

    <div class="select-flex">
      <label for="select">Filter by genre:</label>
      <br />
      <div class="select">
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
    resetSelect() {
      this.value = "All";
    },
  },
};
</script>

<style scoped lang="scss">
@import "../style/searchbar";
</style>
