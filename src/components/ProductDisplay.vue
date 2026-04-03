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
        <p class="product-title">{{ product.title }}</p>
        <p>{{ product.category }}</p>
        <p>{{ product.rating.rate }}</p>
        <p>{{ product.description }}</p>
        <p class="product-price">${{ product.price }}</p>
        <button class="btn-buy">Buy Now</button>
        <button class="btn-next" @click="handleNext()">Next Product</button>
      </div>
    </div>
  </div>

  <button class="btn-buy">Buy Now</button>
  <button class="btn-next" @click="handleNext()">Next Product</button>
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
