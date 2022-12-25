<template>
  <main>
    <h2>Add a new product</h2>
    <product-form :owners="owners" :categories="categories"></product-form>
  </main>
</template>

<script>
export default {
  async asyncData({ $axios }) {
    try {
      let categories = $axios.$get("http://localhost:4000/api/category");
      let owners = $axios.$get("http://localhost:4000/api/owner");
      const [catResponse , ownerResponse] = await Promise.all([
        categories,
        owners
      ])
      
      return{
        categories : catResponse.categories,
        owners : ownerResponse.owners
      }

      } catch (error) {
      console.log(error);
    }
  },
};
</script>

<style lang="scss">
main {
  max-width: 50rem;
  margin: 0 auto;
}
</style>
