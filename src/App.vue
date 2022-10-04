<template>
  <div id="app">
    <p v-if="isLoading">Loading...</p>
    <Search @searchRequested="handleSearch" />
    <Preview :gifs="gifs" />
  </div>
</template>

<script>
import Preview from "./components/Preview.vue";
import Search from "./components/Search.vue";
export default {
  components: { Search, Preview },
  name: "app",
  data() {
    return {
      isLoading: true,
      gifs: []
    };
  },
  methods: {
    handleSearch(query) {
      this.gifs = [];
      this.isLoading = true;
      fetch(
        `https://api.giphy.com/v1/gifs/search?q=${query}&api_key=57VVkqEbr5L8i3xHXhIejE6OYloA967H&limit=25&rating=g&limit=25`
      )
        .then(res => {
          return res.json();
        })
        .then(res => {
          this.gifs = res.data;
          this.isLoading = false;
        });
    }
  },
  created() {
    fetch(
      `https://api.giphy.com/v1/gifs/trending?api_key=57VVkqEbr5L8i3xHXhIejE6OYloA967H&limit=25&rating=g&limit=25`
    )
      .then(res => {
        return res.json();
      })
      .then(res => {
        this.gifs = res.data;
        this.isLoading = false;
      });
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
</style>
