<template>
  <div class="book-card">
    <p class="title">{{ book.volumeInfo.title }}</p>
    <img
      :src="book.volumeInfo.imageLinks.smallThumbnail"
      v-if="imageAvailable(book)"
    />
    <img src="../assets/small-book.jpg" v-if="!imageAvailable(book)" />
    <p class="description">{{ book.volumeInfo.description }}</p>
  </div>
</template>

<script>
export default {
  name: "BookCard",
  props: ["book"],
  methods: {
    imageAvailable(book) {
      if (
        book.volumeInfo.imageLinks !== undefined &&
        book.volumeInfo.imageLinks.smallThumbnail !== undefined
      ) {
        return true;
      } else {
        return false;
      }
    },
  },
};
</script>

<style scoped>
.book-card {
  background-color: white;
  padding: 10px;
  border-bottom: 1px #cccccc dotted;
}
.title {
  font-weight: bold;
  font-size: 1.1rem;
}

/* .description {
  text-overflow: ellipsis;
  white-space: nowrap;
  overflow: hidden;
} */
</style>
