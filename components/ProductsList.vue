<template>
  <ul class="products d-flex">
    <product-item v-for="product in products" :key="product._id" :product="product"></product-item>
  </ul>
</template>

<script>
export default {
    props : ['products']
};
</script>

<style lang="scss" scoped>
.products {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(15rem, 25rem));
  align-items: center;
  justify-items: center;
  grid-gap: 1rem;
}
</style>
