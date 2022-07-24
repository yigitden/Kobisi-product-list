<template>
  <transition name="modal-animation">
    <div v-show="modalActive" class="modal row justify-center align-center">
      <transition name="modal-animation-inner">
        <div v-show="modalActive" class="modal-inner">
          <div class="row justify-flex-end modal-close">
            <i @click="close">x</i>
          </div>
          <div class="row">
            <div
              class="modal-all-images col-6-md d-flex-xs flex-column-reverse-xs flex-row-md"
            >
              <div
                class="modal-three-images col-2-xs col-2-md d-flex-xs flex-column-md flex-row-xs justify-space-evenly-md"
              >
                <img v-bind:src="`https:${product.image}`" />
                <img v-bind:src="`https:${product.image}`" />
                <img v-bind:src="`https:${product.image}`" />
              </div>
              <div
                class="modal-product-image col-12-xs col-10-md align-center justify-center column"
              >
                <img v-bind:src="`https:${product.image}`" />
              </div>
            </div>
            <div class="col-12-xs col-6-md">
              <div class="modal-product-body">
                <div class="modal-product-name">
                  <h1>{{ product.name }}</h1>
                  <h6>SKU: {{ product.id }}</h6>
                </div>
                <div class="modal-product-description">
                  {{ product.description }}
                </div>
                <div class="modal-product-price">
                  <h5>{{ product.oldPrice }}</h5>
                  <h3>{{ product.price }}</h3>
                </div>
              </div>
              <div
                class="modal-product-count row align-center justify-space-between"
              >
                <ProductCount />
              </div>
            </div>
          </div>
        </div>
      </transition>
    </div>
  </transition>
</template>

<script>
import ProductCount from "./ProductCount.vue";
export default {
  name: "ProductModal",
  components: { ProductCount },

  props: ["modalActive", "product"],
  setup(props, { emit }) {
    const close = () => {
      emit("close");
    };
    return { close };
  },
};
</script>

<style lang="scss" scoped>
.modal {
  overflow-y: auto;
  height: 100vh;
  width: 100vw;
  position: fixed;
  top: 0;
  left: 0;
  background-color: rgba(255, 255, 255, 0.7);

  .modal-inner {
    position: relative;
    max-width: 840px;
    width: 80%;
    box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1),
      0 2px 4px -1px rgba(0, 0, 0, 0.06);
    background-color: $lightgray;
    padding: $base-padding * 5 $base-padding * 1.5;
    i {
      position: absolute;
      top: 15px;
      right: 15px;
      font-size: $font-size-lg;
      cursor: pointer;
      &:hover {
        color: crimson;
      }
    }
    img {
      width: 80%;
      max-width: 200px;
    }
  }
  .modal-close {
    cursor: pointer;
  }
  .modal-three-images img {
    margin-right: $base-margin/2;
  }
}
.modal-product-price h5 {
  color: $fire;
  text-decoration: line-through;
}
.modal-animation-enter-active,
.modal-animation-leave-active {
  transition: opacity 0.3s cubic-bezier(0.52, 0.02, 0.19, 1.02);
}
.modal-animation-enter-from,
.modal-animation-leave-to {
  opacity: 0;
}
.modal-animation-inner-enter-active {
  transition: all 0.3s cubic-bezier(0.52, 0.02, 0.19, 1.02) 0.15s;
}
.modal-animation-inner-leave-active {
  transition: all 0.3s cubic-bezier(0.52, 0.02, 0.19, 1.02);
}
.modal-animation-inner-enter-from {
  opacity: 0;
  transform: scale(0.8);
}
.modal-animation-inner-leave-to {
  transform: scale(0.8);
}
</style>
