<template>

  <div class="card">
    <div className="card-image row justify-center  ">
      <img v-bind:src="`https:${product.image}`" />
    </div>
    <div class="card-body">
      <div class="product-name row justify-center align-center">
        {{ product.name }}
      </div>
      <div class="product-price row justify-center">{{ product.price }}</div>
    </div>
  </div>
</template>

<script>
export default {
  name: "ProductCard",
  props: {
    product: Object,
  },
};
</script>

<style lang="scss" scoped>
.card {
  border: $base-border-thickness solid $gray;
  border-radius: $base-border-radius/10;
  box-shadow: $base-box-shadow;
  margin: $base-margin;
  min-height: 260px;
  cursor: pointer;
  padding: $base-padding; 
  height: 100%;
}

.card,
.card-image {
  overflow: hidden;

}
img {

    width: 80%;
    height: auto;
}
.product-name {
  font-size: $base-font-size * 1.1;
  min-height: 70px;
  text-align: center;
}
.product-price {
  font-size: $base-font-size * 1.1;
  font-weight: bold;
  min-height: 10px;
}
</style>
