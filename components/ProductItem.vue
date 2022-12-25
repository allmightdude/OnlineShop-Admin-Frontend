<template>
  <li class="product">
    <base-card>
      <!-- product image -->
      <a href="#" class="product__image">
        <img :src="product.photo" alt="" />
      </a>

      <div class="pd-1">
        <!-- product title -->
        <h3>{{product.title}}</h3>

        <div class="d-flex product__reviews mt-1">
          <div class="product__stars">
            <i class="fa fa-star"></i>
            <i class="fa fa-star"></i>
            <i class="fa fa-star"></i>
            <i class="fa fa-star"></i>
            <i class="fa fa-star"></i>
          </div>

          <div class="product__reviews-numbers">({{product.reviews.length}})</div>
        </div>
        <!-- product price -->
        <span class="product__price mt-1">$ {{product.price}}</span>

        <div class="actions mt-2">
          <base-button size="sm-size" mode="grey">update</base-button>
          <base-button size="sm-size" mode="grey">delete</base-button>
        </div>
      </div>
    </base-card>
  </li>
</template>

<script>
export default {
    props :['product']
}
</script>

<style lang="scss" scoped>
.product {
  &__item {
  }

  &__image {
    img {
      width: 100%;
      object-fit: contain;
    }
  }

  &__reviews {
    align-items: center;
  }
  &__reviews-numbers {
    color: #2c3e50;
  }

  &__price {
    color: #c0392b;
  }
}

.fa-star {
  color: #f1c40f;
}
</style>
