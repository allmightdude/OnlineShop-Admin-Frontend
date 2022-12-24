<template>
  <ul class="products d-flex">
    <product-item></product-item>
    <product-item></product-item>
    <product-item></product-item>
    <product-item></product-item>
    <product-item></product-item>
  </ul>
</template>

<script>
import ProductItem from "./ProductItem.vue";
export default {
  components: {
    ProductItem,
  },
};
</script>

<style lang="scss" scoped>
.products {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(15rem, 1fr));
  align-items: center;
  justify-items: center;
  grid-gap: 1rem;
}
</style>
