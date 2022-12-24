<template>
  <form class="form mt-2">
    <!-- category dropdown -->
    <div class="form__control">
      <label for="category">Category</label>
      <select>
        <option value="1">1</option>
        <option value="1">2</option>
      </select>
    </div>

    <!-- owner dropdown -->
    <div class="form__control">
      <label for="category">Owner</label>
      <select>
        <option value="1">1</option>
        <option value="1">2</option>
      </select>
    </div>

    <div class="form__control">
      <label for="title">Title</label>
      <input type="text" class="form__input" />
    </div>

    <div class="form__control">
      <label for="price">Price</label>
      <input type="number" class="form__input" />
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

        <input id="file-input" type="file" />
        <p>name of image</p>
      </div>
    </div>

    <div class="form__control">
      <base-button mode="orange">Add Product</base-button>
    </div>
  </form>
</template>

<style lang="scss">
.image-upload > input {
  display: none;
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
</style>
