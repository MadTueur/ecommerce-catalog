<template>
  <ProductDisplay />
  <div>
    <button @click="nextProduct()">Next Product</button>
  </div>
</template>

<script>
import ProductDisplay from "./components/ProductDisplay.vue";

export default {
  name: "App",
  components: {
    ProductDisplay,
  },
  data() {
    return {
      productIndex: 1,
      product: null,
    };
  },
  methods: {
    nextProduct() {
      this.productIndex++;
      if (this.productIndex > 20) {
        this.productIndex = 1;
      }
      this.fetchProduct();
    },
    fetchProduct() {
      fetch(`https://fakestoreapi.com/products/${this.productIndex}`)
        .then((response) => response.json())
        .then((data) => {
          console.log(data);
          if (
            data.category === "men's clothing" ||
            data.category === "women's clothing"
          ) {
            this.product = data;
          }
        });
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
