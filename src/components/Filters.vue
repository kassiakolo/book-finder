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
        <b-form-datepicker
          v-model="publishedDate"
          class="form"
          placeholder="Published Date"
        ></b-form-datepicker>
        <b-form-group class="form"
          ><b-form-radio v-model="language" name="language" value="PL"
            >PL</b-form-radio
          >
          <b-form-radio v-model="language" name="language" value="EN"
            >EN</b-form-radio
          >
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
      publishedDate: "",
      language: "",
    };
  },
  methods: {
    filter() {
      const newFilter = {
        author: this.author,
        publishedDate: this.publishedDate,
        language: this.language,
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
