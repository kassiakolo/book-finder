<template>
  <div id="app">
    <div class="container">
      <img src="../assets/books-row.jpg" />
      <div class="find-your-book">
        <div class="book-search">
          <div>
            <Search v-on:new-search="search" />
            <b-alert v-if="!this.books" show>No search results.</b-alert>
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
      const { title, author, language } = newSearch;
      let url = "https://www.googleapis.com/books/v1/volumes?";
      let query = [];
      if (title !== undefined && title !== "") {
        query.push(`intitle:${title}`);
      }
      if (author !== undefined && author !== "") {
        query.push(`inauthor:${author}`);
      }
      url += "q=" + query.join("+");
      if (language !== undefined && language !== "") {
        url += `&langRestrict=${language}`;
      }
      url += `&maxResults=40`;
      console.log(url);
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
