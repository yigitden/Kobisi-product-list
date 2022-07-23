<template>
  <transition name="modal-animation">
    <div v-show="modalActive" class="modal row justify-center align-center">
      <transition name="modal-animation-inner">
        <div v-show="modalActive" class="modal-inner">
       
       
          <!-- Modal Content -->
          
          <button @click="close" type="button">Close</button>
        </div>
      </transition>
    </div>
  </transition>
</template>

<script>
export default {
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
    max-width: 640px;
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
    button {
      padding: $base-padding*1.5 $base-padding*2.5;
      border: none;
      font-size: $base-font-size;
      background-color: crimson;
      color: #fff;
      cursor: pointer;
    }
  }
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