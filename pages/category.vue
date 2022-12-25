<template>
  <main class="main-auto">
    <form class="form mt-2" @submit.prevent="addCategory">
      <div class="form__control">
        <label for="title">Title</label>
        <input type="text" class="form__input" v-model="title" />
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
      title: "",
      isLoading: false,
    };
  },
  methods: {
    async addCategory() {
      this.isLoading = true;
      try {
        let response = await this.$axios.$post(
          "http://localhost:4000/api/category",
          { title: this.title }
        );
        this.$router.replace('/')
      } catch (error) {
        console.log(error);
      }
      this.isLoading = false;
    },
  },
};
</script>

<style lang="scss"></style>
