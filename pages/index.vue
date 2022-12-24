<template>
  <main>
    <h1>All products</h1>
    <div class="actions mt-2">
      <base-button mode="orange" size="lg-size">Add new product</base-button>
      <base-button mode="border" size="lg-size">Add new category</base-button>
      <base-button mode="border" size="lg-size">Add new owner</base-button>
    </div>
  </main>
</template>

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

  .mt-1{margin-top: 1rem;}
  .mt-2{margin-top: 2rem;}
  .mt-3{margin-top: 3rem;}

  h1{
    color: #707070;
  }
</style>
