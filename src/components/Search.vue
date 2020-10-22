<template>
  <div class="find-your-book">
    <h1 class="col">What title are you looking for?</h1>
    <form class='col' @submit.prevent="search">
      <input class="col"
        type="text"
        v-model="title"
        name="title"
        placeholder="Book title..."
      />
      <b-button class='col' type="submit">Search</b-button>
    </form>

  </div>
</template>

<script>
export default {
  name: "Search",
  data() {
    return {
      title: "",
    };
  },
  methods: {
    search() {
      const newSearch = {
        title: this.title,
      };
      this.$emit("new-search", newSearch);
      this.title = "";
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
h1{
  padding-bottom: 20px;
}

</style>
