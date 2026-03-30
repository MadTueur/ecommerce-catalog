<template>
  <div
    class="page"
    :class="{
      'men-section': product.category === 'men\'s clothing',
      'women-section': product.category === 'women\'s clothing',
    }"
  >
    <div class="card">
      <img :src="product.image" />
      <div class="product-info">
        <p>{{ product.title }}</p>
        <p>{{ product.category }}</p>
        <p>{{ product.rating.rate }}</p>
        <p>{{ product.description }}</p>
        <p>${{ product.price }}</p>
        <button>Buy Now</button>
        <button @click="handleNext()">Next Product</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "ProductDisplay",
  props: {
    product: Object,
  },

  methods: {
    handleNext() {
      this.$emit("next-product");
    },
  },
};
</script>
