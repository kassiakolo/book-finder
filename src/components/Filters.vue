<template>
  <div id="filters">
    <div>
      <!-- Using value -->
      <b-button class="button" v-b-modal="'my-modal'">Filters</b-button>

      <!-- The modal -->
      <b-modal id="my-modal" title="Let's give more details..." @ok="filter">
        <b-form-input
          v-model="authorInput"
          class="form"
          placeholder="Author"
        ></b-form-input>
        <b-form-group class="form"
          ><b-form-radio v-model="languageInput" name="language" value="pl"
            >Polish</b-form-radio
          >
          <b-form-radio v-model="languageInput" name="language" value="en"
            >English</b-form-radio
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
      authorInput: this.author,
      languageInput: this.language,
    };
  },
  props: ["author", "language"],
  watch: {
    // eslint-disable-next-line no-unused-vars
    author: function(newVal, oldVal) {
      this.authorInput = newVal;
    },
    // eslint-disable-next-line no-unused-vars
    language: function(newVal, oldVal) {
      this.languageInput = newVal;
    },
  },
  methods: {
    filter() {
      const newFilter = {
        author: this.authorInput,
        language: this.languageInput,
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
