<template>
  <transition name="modal-animation">
    <div v-show="modalActive" class="modal row justify-center align-center">
      <transition name="modal-animation-inner">
        <div v-show="modalActive" class="modal-inner">
       
       
          <!-- Modal Content -->
          <div @click="close" class="row justify-flex-end modal-close" >X</div>
          <div class="row">
            <div class="col-12-lg"></div>
            <div class="col-1-lg">

            </div>
            <div class="col-5-lg modal-product-image justify-center">
                 <img v-bind:src="`https:${product.image}`" />

            </div>
            <div class="col-6-lg">
                <div class="modal-product-body">
                    <div class="modal-product-name"><h1>{{product.name}}</h1>  <h6>SKU: {{product.id}}</h6></div>
                    <div class="modal-product-description">{{product.description}}</div>
                    <div class="modal-product-price"><h5>{{product.oldPrice}}</h5>  <h3>{{product.price}}</h3></div>
                </div>
                <div class="modal-product-count row align-center justify-space-between">
                 <Count/>
                </div>
            </div>
          </div>
          
        </div>
      </transition>
    </div>
  </transition>
</template>

<script>
import Count from './Count.vue'
export default {
  components:{Count},
  props: ["modalActive","product"],
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
    box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1), 0 2px 4px -1px rgba(0, 0, 0, 0.06);
    background-color: $lightgray;
    padding: $base-padding*5 $base-padding*1.5;
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
    img{
        width:60%
    }

  }
    .modal-close{
         cursor:pointer
    }

}
.modal-product-price h5{
    color:$fire;
    text-decoration:line-through;
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