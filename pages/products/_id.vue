<template>
  <main class="main-auto">
    <h2>Update {{ product.title }}</h2>
    <form class="form mt-2" @submit.prevent="addProduct">
      <!-- category dropdown -->
      <div class="form__control">
        <label for="category">Category</label>
        <select v-model="catID">
          <option v-for="cat in categories" :key="cat._id" :value="cat._id">
            {{ cat.title }}
          </option>
        </select>
      </div>

      <!-- owner dropdown -->
      <div class="form__control">
        <label for="category">Owner</label>
        <select v-model="ownerID">
          <option v-for="owner in owners" :key="owner._id" :value="owner._id">
            {{ owner.name }}
          </option>
        </select>
      </div>

      <div class="form__control">
        <label for="title">Title</label>
        <input type="text" class="form__input" v-model="title" />
      </div>

      <div class="form__control">
        <label for="price">Price</label>
        <input type="number" class="form__input" v-model="price" />
      </div>

      <div class="form__control">
        <label for="stockQuantity">StockQuantity</label>
        <input type="number" class="form__input" v-model="stockQuantity" />
      </div>

      <div class="form__control">
        <label for="description">Description</label>
        <textarea id="description" rows="5" v-model="description"></textarea>
      </div>

      <!-- Photo  -->

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
        <base-button class="addProduct" mode="orange">
          <span>Add Product</span>
        </base-button>
        <!-- 
        <div class="loader">
          <img src="../static/img/loader.gif" alt="" />
        </div> -->
      </div>
    </form>
  </main>
</template>

<script>
export default {
  async asyncData({ $axios, params }) {
    let product = $axios.$get(
      `http://localhost:4000/api/products/${params.id}`
    );
    let categories = $axios.$get("http://localhost:4000/api/category");
    let owners = $axios.$get("http://localhost:4000/api/owner");

    const [catResponse, ownerResponse, productResponse] = await Promise.all([
      categories,
      owners,
      product,
    ]);

    return {
      categories: catResponse.categories,
      owners: ownerResponse.owners,
      product: productResponse.product,
    };
  },
  data() {
    return {
      catID: null,
      ownerID: null,
      title: "",
      price: null,
      description: "",
      stockQuantity: null,
      selectedFile: null,
      fileName: "",
    };
  },

  mounted() {
    this.catID = this.product.categoryID;
    this.ownerID = this.product.ownerID;
    this.title = this.product.title;
    this.price = this.product.price;
    this.stockQuantity = this.product.stockQuantity;
    this.description = this.product.description;
  },

  methods: {
    async addProduct() {
      try {
        this.isLoading = true;
        let data = new FormData();

        data.append("categoryID", this.catID);
        data.append("ownerID", this.ownerID);

        data.append("title", this.title);
        data.append("price", this.price);
        data.append("description", this.description);
        data.append("stockQuantity", this.stockQuantity);
        data.append("photo", this.selectedFile);

        let result = await this.$axios.$post(
          "http://localhost:4000/api/products",
          data
        );
        this.isLoading = false;
        this.$router.replace("/");
      } catch (error) {
        console.log(error);
      }
    },
    onFileSelected(e) {
      this.selectedFile = e.target.files[0];
      this.fileName = e.target.files[0].name;
    },
  },
};
</script>

<style lang="scss"></style>
