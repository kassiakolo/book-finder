<template>
  <div>
    <div v-bind:key="book.id" v-for="book in pageBooks">
      <BookCard v-bind:book="book" />
    </div>
    <b-pagination v-if="books.length > 0"
      v-model="currentPage"
      :total-rows="rows"
      :per-page="perPage"
      aria-controls="my-table"
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
  data() {
    return {
      currentPage: 1,
      perPage: 3,
    };
  },
  computed: {
    pageBooks() {
      return this.books.slice(
        (this.currentPage - 1) * this.perPage,
        this.currentPage * this.perPage
      );
    },
    rows() {
      return this.books.length;
    },
  },
};
</script>

<style scoped></style>
