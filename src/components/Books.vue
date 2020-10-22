<template>
  <div>
    <div v-bind:key="book.id" v-for="book in books">
      <BookCard v-bind:book="book"/>
    </div>
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
};
</script>

<style scoped></style>
