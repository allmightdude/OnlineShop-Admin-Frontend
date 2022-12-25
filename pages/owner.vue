<template>
  <main class="main-auto">
    <form class="form mt-2" @submit.prevent="addCategory">
      <div class="form__control">
        <label for="name">name</label>
        <input type="text" class="form__input" v-model="name" />
      </div>

      <div class="form__control">
        <label for="about">About</label>
        <input type="text" class="form__input" v-model="about" />
      </div>

      <div class="form__control">
        <label>Add Photo</label>
        <div class="image-upload">
          <label for="file-input">
            <i class="fa fa-plus"></i>
          </label>

          <input id="file-input" type="file" @change="onFileSelected" />
          <p>{{ fileName }}</p>
        </div>
      </div>

      <div class="form__control">
        <base-button v-if="!isLoading" class="addProduct" mode="orange">
          <span>Add Product</span>
        </base-button>

        <div v-else class="loader">
          <img src="../static/img/loader.gif" alt="" />
        </div>
      </div>
    </form>
  </main>
</template>

<script>
export default {
  data() {
    return {
      name: "",
      about: "",
      selectedFile: null,
      fileName: "",

      isLoading: false,
    };
  },
  methods: {
    async addCategory() {
      this.isLoading = true;
      try {
        let data = new FormData();

        data.append("name", this.name);
        data.append("about", this.about);
        data.append("photo", this.selectedFile);
        let response = await this.$axios.$post(
          "http://localhost:4000/api/owner",
          data
        );
        console.log(response);
        this.$router.replace("/");
      } catch (error) {
        console.log(error);
      }
      this.isLoading = false;
    },
    onFileSelected(e) {
      this.selectedFile = e.target.files[0];
      this.fileName = e.target.files[0].name;
    },
  },
};
</script>

<style lang="scss"></style>
