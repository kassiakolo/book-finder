<template>
  <div id="app">
    <div class="container">
      <img src="../assets/books-row.jpg" />
      <div class="find-your-book">
        <div class="book-search">
          <div>
            <Search v-on:new-search="search" />
          </div>
          <Books v-bind:books="books" />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Books from "./Books";
import Search from "./Search";
import axios from "axios";

export default {
  name: "Home",
  components: {
    Books,
    Search,
  },

  data() {
    return {
      books: [],
    };
  },
  methods: {
    search(newSearch) {
      const {title, selectedCategories} = newSearch;
      const url = `https://www.googleapis.com/books/v1/volumes?q=${title}+subject:${selectedCategories}`
      console.log(url)
      axios
        .get(url)
        .then((res) => {
          console.log(res);
          this.books = res.data.items;
        })
        .catch((err) => console.log(err));
    },
  },
};
</script>

<style scoped>
img {
  width: 100%;
}
</style>
