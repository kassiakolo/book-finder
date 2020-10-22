<template>
  <div class="book-card">
    <p class="title">{{ book.volumeInfo.title }}</p>
    <img :src="book.volumeInfo.imageLinks.smallThumbnail" />
    <p class="description">{{ book.volumeInfo.description }}</p>
  </div>
</template>

<script>
export default {
  name: "BookCard",
  props: ["book"],
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
