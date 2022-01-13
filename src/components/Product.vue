<template>
  <main class="product">
    <div class="wrapper">
      <ProductImages/>
      <ProductDetails/>
    </div>
  </main>
</template>

<script>
import ProductImages from "./ProductImages";
import ProductDetails from "./ProductDetails";

export default {
  name: "Product",
  components: {
    ProductDetails,
    ProductImages,
  },
  mounted: () => {},
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
@media only screen and (min-width: 750px) {

  .product {
    margin-top: 4rem;
  }

  .wrapper {
    display: flex;
    align-items: center;
    justify-content: space-between;
    max-width: 1000px;
    margin: 0 auto;
  }

}
</style>
