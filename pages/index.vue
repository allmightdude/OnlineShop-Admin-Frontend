<template>
  <main>
    <h1>All products</h1>
    <div class="actions mt-2">
      <base-button mode="orange" size="lg-size">Add new product</base-button>
      <base-button mode="border" size="lg-size">Add new category</base-button>
      <base-button mode="border" size="lg-size">Add new owner</base-button>
    </div>

    <!-- Products List -->
    <products-list class="mt-2" :products="products"></products-list>
  </main>
</template>

<script>
export default {
  async asyncData({ $axios }) {
    try {
      let response = await $axios.get(`http://localhost:4000/api/products`);
      const products = response.data.products;
      return {
        products,
      };
    } catch (error) {
      console.log(error);
    }
  },
};
</script>

<style lang="scss">

</style>
