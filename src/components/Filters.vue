<template>
  <div id="filters">
    <div>
      <!-- Using value -->
      <b-button class="button" v-b-modal="'my-modal'">Filters</b-button>

      <!-- The modal -->
      <b-modal id="my-modal">
        <h4>Let's give more details...</h4>
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
    };
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
