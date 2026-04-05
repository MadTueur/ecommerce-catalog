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
        <div class="category-rating">
          <p>{{ product.category }}</p>
          <div class="rating">
            <span>{{ product.rating.rate }}/5</span>
            <div class="stars">
              <span
                v-for="n in 5"
                :key="n"
                :class="
                  n <= Math.round(product.rating.rate) ? 'star filled' : 'star'
                "
              ></span>
            </div>
          </div>
        </div>
        <hr class="divider" />
        <p>{{ product.description }}</p>
        <hr class="divider-bottom" />
        <p class="product-price">${{ product.price }}</p>
        <div class="btn-group">
          <button class="btn-buy">Buy Now</button>
          <button class="btn-next" @click="handleNext()">Next Product</button>
        </div>
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
