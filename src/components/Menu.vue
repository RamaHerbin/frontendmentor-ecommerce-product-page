<template>
  <transition name="slide">
   <aside v-if="show" id="aside-menu">
		  <div class="aside-wrapper">

		  </div>
	  </aside>
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
    }
  },
};
</script>

<style scoped>

#aside-menu {
	display: flex;
	position: fixed;
	left: 0;
	top: 0;
	bottom: 0;
	width: 66vw;

	background-color: #fff;
}

.slide-enter-active, .slide-leave-active {
  transition: transform .8s cubic-bezier(.16,1,.3,1);
}

.slide-enter-from, .slide-leave-to {
transform: translateX(-100%);
}
.aside-wrapper {
    padding: 1rem;
}
</style>
