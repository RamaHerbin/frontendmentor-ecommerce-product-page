<template>
  <div class="cart-modal" v-if="show" role="dialog" aria-labelledby="modalTitle">
    <section class="cartHeader">Cart</section>
    <section class="cartContent">
      <p>Your cart is empty</p>
    </section>
  </div>
</template>

<script>
export default {
  name: "CartModal",
  data() {
      return {
          show: false
      };
  },
  mounted: () => {},
  methods: {
    closeModal() {
      this.show = false;
    //   document.querySelector("body").classList.remove("overflow-hidden");
    },
    openModal() {
      this.show = true;
    //   document.querySelector("body").classList.add("overflow-hidden");
    },
  },
};
</script>

<style scoped>

.cart-modal {
    box-shadow: 0px 10px 49px 26px rgba(0,0,0,0.1);
    position: relative;
    left: -200px;
    top: 100px;
    max-width: 360px;
}

.cart-modal section {
    padding: 1rem;
}

.cartHeader {
    border-bottom: solid 1px rgb(176, 176, 176);
}

.cartContent p {
  padding: 1rem;
}
</style>
