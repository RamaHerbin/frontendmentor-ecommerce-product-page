<template>
  <transition v-on:enter="enter" v-on:leave="leave">
    <div class="cart-modal" v-if="show" role="dialog" aria-labelledby="modalTitle">
      <section class="cartHeader">Cart</section>
      <section class="cartContent">
        <p>Your cart is empty</p>
      </section>
    </div>
  </transition>
</template>

<script>
import { gsap } from "../assets/gsap/all.js";

export default {
  name: "CartModal",
  data() {
    return {
      show: false,
    };
  },
  mounted: () => {},
  methods: {
    closeModal() {
      this.show = false;
    },
    openModal() {
      this.show = true;
    },
    enter: function (el, done) {
      gsap.from(el, { duration: 0.5, autoAlpha: 0, scale: 0.8, ease: "power4.inOut", onComplete: () => gsap.set(el, { clearProps: "all" }) });
    },
    leave: function (el, done) {
      gsap.to(el, { duration: 0.3, autoAlpha: 0, scale: 0.8, ease: "power4.inOut", onComplete: done });
    },
  },
};
</script>

<style scoped>
.cart-modal {
  box-shadow: 0px 10px 49px 26px rgba(0, 0, 0, 0.1);
  background-color: #ffffff;
  border-radius: 5px;
  position: absolute;
  top: calc(2.5vw + 66px);
  left: 2.5vw;
  width: 95vw;
  transform: translateX(0);
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

@media only screen and (min-width: 650px) {
  .cart-modal {
    width: 360px;
    transform: translateX(-80%);
    top: 40px;
    left: unset;
  }
}

@media only screen and (min-width: 1260px) {
  .cart-modal {
    /* width: 360px; */
    transform: translateX(-50%);
    /* top: 40px; */
    /* left: unset; */
  }
}
</style>
