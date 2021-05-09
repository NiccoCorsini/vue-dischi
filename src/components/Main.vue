<template>
  <div class="macrocontainer">
    <Searchbar
      @research="filterSearch"
      :genres="genres"
      @options="selectGenre"
      @reset="resetSearch"
    />
    <div v-if="!loading" class="container-total">
      <div
        v-for="(disco, index) in filteredDiscs"
        :key="disco.title + index"
        class="disk-container"
      >
        <Disc :details="disco" />
      </div>
    </div>
    <div v-else class="spinner">
      <Spinner>
        {{ library }}
      </Spinner>
    </div>
  </div>
</template>

<script>
import axios from "axios";
import Searchbar from "../components/Searchbar";
import Disc from "../components/Disc";
import Spinner from "../components/Spinner";

export default {
  name: "Main",
  components: {
    Searchbar,
    Disc,
    Spinner,
  },
  data() {
    return {
      ApiUrl: "https://flynn.boolean.careers/exercises/api/array/music",
      discs: [],
      loading: true,
      library: "libreria musicale",
      filteredDiscs: [],
      genres: [],
    };
  },
  created() {
    this.getApi();
  },
  updated() {
    this.genreExtractor();
    this.searchType();
  },
  methods: {
    getApi() {
      axios
        .get(this.ApiUrl)
        .then((res) => {
          this.discs = res.data.response;
          setTimeout(() => {
            this.loading = false;
          }, 2000);
        })
        .catch((err) => {
          console.log("Error", err);
        });
    },
    filterSearch(text) {
      return (this.filteredDiscs = this.discs.filter(
        (disc) =>
          disc.title.toLowerCase().includes(text.toLowerCase()) ||
          disc.author.toLowerCase().includes(text.toLowerCase())
      ));
    },
    resetSearch(reset) {
      if (reset == "") {
        return (this.filteredDiscs = this.discs);
      }
    },
    selectGenre(value) {
      return (this.filteredDiscs = this.discs.filter(
        (genre) => genre.genre == value
      ));
    },
    genreExtractor() {
      this.discs.forEach((genre) => {
        if (!this.genres.includes(genre.genre)) {
          this.genres.push(genre.genre);
        }
      });
    },
    searchType() {
      if (this.filteredDiscs.length == 0) {
        return (this.filteredDiscs = this.discs);
      }
    },
  },
};
</script>

<style scoped lang="scss">
@import "../style/main";
</style>
