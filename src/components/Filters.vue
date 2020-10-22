<template>
  <div id="filters">
    <div>
      <!-- Using value -->
      <b-button class="button" v-b-modal="'my-modal'">Filters</b-button>

      <!-- The modal -->
      <b-modal id="my-modal" title="Let's give more details..." @ok="filter">
        <b-form-input
          v-model="author"
          class="form"
          placeholder="Author"
        ></b-form-input>
        <b-form-input
          v-model="language"
          class="form"
          placeholder="Language"
        ></b-form-input>
        <b-form-datepicker
          v-model="publishedDate"
          class="form"
          placeholder="Published Date"
        ></b-form-datepicker>
        <b-form-group>
          <b-form-checkbox-group
            v-model="selectedCategories"
            :options="categories"
            class="form"
          ></b-form-checkbox-group>
        </b-form-group>
      </b-modal>
    </div>
  </div>
</template>

<script>
export default {
  name: "Filters",
  data() {
    return {
      author: "",
      language: "",
      publishedDate: "",
      selectedCategories: [],
      categories: [
        { text: "Biography & Autobiography", value: "biography & autobiography" },
        { text: "Cooking", value: "cooking" },
        { text: "Drama", value: "drama" },
        { text: "Education", value: "education" },
        { text: "Fiction", value: "fiction" },
        { text: "History", value: "history" },
        { text: "Poetry", value: "poetry" },
        { text: "Thriller", value: "thriller" },
        { text: "Travel", value: "travel" },
        { text: "Science", value: "science" },
        { text: "Sport & Recreation", value: "sport & recreation" },
      ],
    };
  },
  methods: {
    filter() {
      const newFilter = {
        author: this.author,
        language: this.language,
        publishedDate: this.publishedDate,
        selectedCategories: this.selectedCategories,
      };
      this.$emit("new-filter", newFilter);
    },
  },
};
</script>

<style scoped>
h4 {
  padding-bottom: 20px;
}
.form {
  margin: 10px 0;
  padding: 10px;
  border: 0;
  box-shadow: 0 0 15px 4px rgba(0, 0, 0, 0.06);
}

.button {
  background-color: whitesmoke;
  color: gray;
  width: 300px;
  border-color: rgb(226, 223, 223);
}
</style>
