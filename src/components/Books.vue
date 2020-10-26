<template>
  <div>
    <div v-bind:key="book.id" v-for="book in pageBooks">
      <BookCard v-bind:book="book" />
    </div>
    <b-pagination
      v-if="books !== undefined && books.length > 0"
      v-model="currentPage"
      :total-rows="rows"
      :per-page="perPage"
    ></b-pagination>
  </div>
</template>

<script>
import BookCard from "./BookCard.vue";

export default {
  name: "Books",
  components: {
    BookCard,
  },
  props: ["books"],
  watch: {
     // eslint-disable-next-line no-unused-vars
    books: function(newVal, oldVal) {
      this.currentPage = 1;
    },
  },
  data() {
    return {
      currentPage: 1,
      perPage: 3,
    };
  },
  computed: {
    pageBooks() {
      if (this.books === undefined) {
        return [];
      }
      return this.books.slice(
        (this.currentPage - 1) * this.perPage,
        this.currentPage * this.perPage
      );
    },
    rows() {
      if (this.books === undefined) {
        return 0;
      }
      return this.books.length;
    },
  },
};
</script>

<style scoped></style>
