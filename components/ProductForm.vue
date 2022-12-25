<template>
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
      <textarea id="description" rows="5"></textarea>
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
      <base-button v-if="!isLoading" class="addProduct" mode="orange">
        <span>Add Product</span>
      </base-button>

      <div v-else class="loader">
        <img src="../static/img/loader.gif" alt="" />
      </div>
    </div>
  </form>
</template>

<script>
export default {
  props: ["categories", "owners"],
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
      isLoading: false,
    };
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
        this.$router.replace('/')

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

<style lang="scss">
.image-upload {
  input {
    display: none;
  }

  label {
    border: 1px dashed #ccc;
    width: 10rem;
    height: 10rem;
    border-radius: 5px;
    display: flex;
    align-items: center;
    justify-content: center;
  }
}

.form {
  width: 100%;
  padding: 1rem;
  border-radius: 5px;
  box-shadow: 0 0.5rem 1rem rgba(0, 0, 0, 0.1);

  label {
    margin: 0.5rem 0;
  }
  &__control {
    width: 100%;
    display: flex;
    margin: 1rem 0;
    flex-direction: column;
  }
}

.fa-plus {
  font-size: 4rem;
  color: #f1c40f;
}

textarea {
  width: 100%;
  resize: none;
}
.addProduct {
  display: flex;
  align-items: center;
  justify-content: center;
}
.loader {
  text-align: center;
  width: 100%;
  height: 100%;
  img{
    width: 4rem;
    height: 4rem;
  }
}
</style>
