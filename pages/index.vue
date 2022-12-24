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
    async asyncData({$axios}){
        try {
            let response = await $axios.get(`http://localhost:4000/api/products`);
            const products = response.data.products;
            return{
                products
            }
        } catch (error) {
            console.log(error);
        }
    },
}
</script>

<style lang="scss">
  * ,
  ::before,
  ::after{
    box-sizing: inherit;
    margin: 0;
    padding: 0;;
  }

  body{
    box-sizing: border-box;
    font-size: 1.5rem;
    padding: 2rem;
  }

  html{
    font-size: 62.5%;
  }

  ul , li{
    list-style: none;
  }
  .d-flex{
    display: flex;
    align-items: center;
    gap: 1rem;
  }
  .mt-1{margin-top: 1rem;}
  .mt-2{margin-top: 2rem;}
  .mt-3{margin-top: 3rem;}

  .pd-1{
    padding: 1rem;
  }
  h1 , h2, h3{
    color: #707070;
  }
</style>
