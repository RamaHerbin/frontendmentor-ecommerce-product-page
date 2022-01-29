<template>
  <Header :cartCount="cartCount" ></Header>
  <Product @dataToApp="onClickChild"></Product>
</template>

<script>
import { gsap } from "./assets/gsap/all.js";
// import DrawSVGPlugin from "./assets/gsap/DrawSVGPlugin.js";
import Header from "@/components/Header";
import Product from "@/components/Product";

export default {
	name: 'App',
  data() {
    return {
      cartCount: 0
    }
  },
  components: {
    Header,
    Product
  },
  mounted() {
    // gsap.registerPlugin(DrawSVGPlugin);

  },
   methods: {
      onClickChild (value) {
          this.cartCount = value;
          console.log('this.cartCount :>> ', this.cartCount);
      }
  }
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Kumbh+Sans:wght@300;400;700&family=Red+Hat+Display:ital,wght@0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,300;1,400;1,500;1,600&display=swap");
html {
  font-size: 100%;
  font-family: "Kumbh Sans";
}

* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

a,
a:hover,
a:focus,
a:active {
  text-decoration: none;
  color: inherit;
}

img {
  user-select: none;
  -webkit-user-drag: none;
}

#app {
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #000;
  max-width: 100%;
}
</style>
