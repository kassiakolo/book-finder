<template>
  <div id="app">
    <div class="container">
      <img src="../assets/books-row.jpg" />
      <div class="find-your-book">
        <div class="book-search">
          <div>
            <Search v-on:new-search="search" />
            <Filters class="filters" />
          </div>
          <Books v-bind:books="books" />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Books from "../components/Books";
import Search from "../components/Search";
import axios from "axios";
import Filters from "../components/Filters";

export default {
  name: "Home",
  components: {
    Books,
    Search,
    Filters,
  },

  data() {
    return {
      books: [],
    };
  },
  methods: {
    search(newSearch) {
      const { title } = newSearch;
      axios
        .get(`https://www.googleapis.com/books/v1/volumes?q=${title}`)
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
.filters {
  text-align: center;
  
}
</style>
