<template>
  <div class="find-your-book">
    <h1 class="col">What title are you looking for?</h1>
    <form class="col" @submit.prevent="search">
      <input
        class="col"
        type="text"
        v-model="title"
        name="title"
        placeholder="Book title..."
      />
      <b-button class="col" type="submit" :disabled="allEmpty()">Search</b-button>
    </form>
    <Filters v-on:new-filter="filter" class="filters" />
  </div>
</template>

<script>
import Filters from "./Filters";

export default {
  name: "Search",
  components: { Filters },
  data() {
    return {
      title: "",
      author: "",
      language: "",
    };
  },
  methods: {
    search() {
      const newSearch = {
        title: this.title,
        author: this.author,
        language: this.language,
      };
      console.log(newSearch);
      this.$emit("new-search", newSearch);
      this.title = "";
      this.author = "";
      this.language = "";
    },
    filter(newFilter) {
      this.author = newFilter.author;
      this.language = newFilter.language;
      console.log(newFilter);
    },
    allEmpty() {
      if (!this.title && !this.author && !this.language) {
        return true;
      } else {
        return false;
      }
    },
  },
};
</script>

<style scoped>
form {
  display: flex;
}
input[type="text"] {
  flex: 10;
  padding: 5px;
}
input[type="submit"] {
  flex: 2;
}
.find-your-book {
  padding-top: 60px;
  padding-bottom: 30px;
}
h1 {
  padding-bottom: 20px;
}
.filters {
  text-align: center;
  padding-top: 15px;
}
</style>
