<template>
  <section id="product-list">
    <div class="container">
      <div class="row">
        <div
          class="product col-12-xs col-6-lg"
          v-for="product of products.slice(0, 1)"
          :key="product.id"
        >
          <ProductCard :product="product" />
        </div>

        <div class="lists col-6-lg row">
          <div
            class="product col-6-xs col-6-lg"
            v-for="product of products.slice(1, 5)"
            :key="product.id"
          >
            <ProductCard :product="product" />
          </div>
        </div>
      </div>

      <div class="row">
        <div class="lists col-6-lg row">
          <div
            class="product col-6-xs col-6-lg"
            v-for="product of products.slice(5, 9)"
            :key="product.id"
          >
            <ProductCard :product="product" />
          </div>
        </div>
        <div
          class="product col-12-xs col-6-lg"
          v-for="product of products.slice(9, 10)"
          :key="product.id"
        >
          <ProductCard :product="product" />
        </div>
      </div>
    </div>
  </section>
</template>

<script>
import axios from "axios";
import ProductCard from "./components/Card/ProductCard.vue";
const API_URL = `http://localhost:3001/product`;
export default {
  name: "App",
  components: { ProductCard },
  data() {
    return {
      products: [],
    };
  },
  created() {
    this.fetchData();
  },
  methods: {
    async fetchData() {
      try {
        const response = await axios.get(`${API_URL}`);
        this.products = response.data;
      } catch (error) {
        alert(error);
      }
    },
  },
};
</script>

<style lang="scss" scoped>
.product {
  padding: $base-padding;
}
</style>
