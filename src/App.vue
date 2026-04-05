<template>
  <div>
    <ProductDisplay
      v-if="product"
      :product="product"
      @next-product="nextProduct()"
    />

    <div v-else class="unavailable">
      <p>This product is unavailable to show</p>
      <button class="btn-next" @click="nextProduct()">Next Product</button>
    </div>
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
      product: {
        title: "Mens Cotton Jacket",
        category: "men's clothing",
        description:
          "Great outerwear jacket for Spring/Autumn/Winter Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris.",
        price: 55.99,
        image: "https://placehold.co/300x400",
        rating: { rate: 4.7 },
      },
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
          } else {
            this.product = null;
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
  margin-top: 0px;
}
</style>
