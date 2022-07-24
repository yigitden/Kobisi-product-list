<template>
  <div
    class="card d-flex-xs flex-column-xs justify-space-evenly-xs"
    @click="handleModal"
  >
    <div className="card-image row justify-center  ">
      <img v-bind:src="`https:${product.image}`" />
    </div>
    <div class="card-body">
      <div class="product-name row justify-center align-center">
        {{ product.name }}
      </div>
      <div class="product-price row justify-center">{{ product.price }}</div>
    </div>
    <button>Hızlı Gözat</button>
  </div>
  <Modal @close="handleModal" :modalActive="modalActive" :product="product" />
</template>

<script>
import { ref } from "vue";
import Modal from "@/components/Modal/ProductModal.vue";
 

export default {
  name: "ProductCard",
  components: { Modal },
  props: {
    product: Object,
  },
  setup() {
    const modalActive = ref(false);
    const handleModal = () => {
      modalActive.value = !modalActive.value;
    };
    return { modalActive, handleModal };
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
  position: relative;

  button {
    position: absolute;
    left: 50%;
    bottom: 50%;
    transform: translateX(-50%);
    height: 40px;
    border: none;
    outline: none;
    background: rgb(81, 81, 81);
    color: #fff;
    font-size: 15px;
    font-weight: 600;
    cursor: pointer;
    opacity: 0;
    transition: 0.6s;
  }
}

.card:hover {
  background-color: rgb(245, 245, 245);
  transition: 0.6s;
  button {
    opacity: 0.8;
    bottom: 50%;
    &:hover {
      opacity: 1;
    }
  }
}

.card-image {
  overflow: hidden;

  width:100%;
}
img {
  width: 50%;
  object-fit: cover;

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
