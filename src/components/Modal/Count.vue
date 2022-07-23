<template>
  <div class="count row align-center justify-space-between">
    <div>
      <button @click="decrementCounter" :disabled="count === 1">-</button>
    </div>
    <div>{{ count }}</div>
    <div><button @click="incrementCounter">+</button></div>
  </div>
  <button>Sepete Ekle</button>
</template>

<script>
export default {
  data() {
    return {
      count: 1,
    };
  },
  methods: {
    incrementCounter: function () {
      this.count += 1;
    },
    decrementCounter: function () {
      this.count -= 1;
    },
  },
};
</script>

<style lang="scss" scoped>
button {
  padding: $base-padding;
  border: none;
  font-size: $base-font-size;
  background-color: $button;
  color: #fff;
  cursor: pointer;
  &:hover {
    transition: 0.3s;
    opacity: 0.9;
  }
}
.count {
  width: 110px;
}
</style>
