<template>
  <transition name="opacity">
    <section @click="closeModal" v-show="show" id="bg-dark">
      <transition name="slide">
        <aside v-show="show" id="aside-menu">
          <div ref="links" class="aside-wrapper">
            <a href="#"><div>Collections</div></a>
            <a href="#"><div>Men</div></a>
            <a href="#"><div>Women</div></a>
            <a href="#"><div>About</div></a>
            <a href="#"><div>Contact</div></a>
          </div>
        </aside>
      </transition>
    </section>
  </transition>
</template>

<script>
import { gsap } from "../assets/gsap/all.js";

export default {
  name: "Menu",
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
      this.test();
      this.linksAnim();
    },
    test() {
      console.log("this.$refs.test :>> ", this.$refs.links.querySelectorAll(".aside-wrapper a span"));
    },
    linksAnim() {
      gsap.from(this.$refs.links.querySelectorAll(".aside-wrapper a div"), { duration: 0.8, y: "20px", ease: "power4.inOut", immediateRender: true });
    },
  },
};
</script>

<style scoped>
#bg-dark {
  position: absolute;
  left: 0;
  top: 0;
  width: 100vw;
  height: 100vh;
  background-color: rgba(0, 0, 0, 0.495);
  z-index: 100;
}

#aside-menu {
  position: fixed;
  left: 0;
  top: 0;
  bottom: 0;
  width: 66vw;
  z-index: 200;
  background-color: #fff;
}

.slide-enter-active,
.slide-leave-active {
  transition: transform 0.8s cubic-bezier(0.16, 1, 0.3, 1);
}
.slide-enter-from,
.slide-leave-to {
  transform: translateX(-100%);
}

.opacity-enter-active,
.opacity-leave-active {
  transition: opacity .25s ease-in-out;
}
.opacity-enter-from,
.opacity-leave-to {
  opacity: 0;
}

.aside-wrapper {
  padding: 2.5rem;
  display: flex;
  justify-content: center;
  flex-direction: column;
}
.aside-wrapper a {
  margin-top: 2rem;
  font-weight: bold;
  font-size: 1.2rem;
  overflow: hidden;
}

@media only screen and (min-width: 850px) {
  #aside-menu {
    display: none;
  }
}
</style>
