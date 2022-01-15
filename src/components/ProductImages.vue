<template>
  <section class="preview">
    <div class="preview-main">
      <div ref="productImagesSlider" class="container-product-images">
        <img src="../assets/image-product-1.jpg" alt="Image product" class="product-images" />
        <img src="../assets/image-product-2.jpg" alt="Image product" class="product-images" />
        <img src="../assets/image-product-3.jpg" alt="Image product" class="product-images" />
        <img src="../assets/image-product-4.jpg" alt="Image product" class="product-images" />
      </div>
      <div class="preview-mobile-selection">
        <div @click="right" class="rounded-button">
          <svg width="12" height="18" xmlns="http://www.w3.org/2000/svg">
            <path d="M11 1 3 9l8 8" stroke="#1D2026" stroke-width="3" fill="none" fill-rule="evenodd" />
          </svg>
        </div>
        <div @click="left" class="rounded-button">
          <svg width="13" height="18" xmlns="http://www.w3.org/2000/svg">
            <path d="m2 1 8 8-8 8" stroke="#1D2026" stroke-width="3" fill="none" fill-rule="evenodd" />
          </svg>
        </div>
      </div>
    </div>
    <div class="preview-selection">
      <div class="preview-image-1 active">
        <img src="../assets/image-product-1-thumbnail.jpg" alt="Image product 1" />
      </div>
      <div class="preview-image-2">
        <img src="../assets/image-product-2-thumbnail.jpg" alt="Image product 2" />
      </div>
      <div class="preview-image-3">
        <img src="../assets/image-product-3-thumbnail.jpg" alt="Image product 3" />
      </div>
      <div class="preview-image-4">
        <img src="../assets/image-product-4-thumbnail.jpg" alt="Image product 4" />
      </div>
    </div>
  </section>
</template>

<script>
import { gsap } from "../assets/gsap/all.js";
import Draggable from "../assets/gsap/Draggable.js";
import InertiaPlugin from "../assets/gsap/InertiaPlugin.js";

gsap.registerPlugin(Draggable, InertiaPlugin);

export default {
  name: "ProductImages",
  data() {
    return {
      show: false,
    };
  },
  mounted() {
    document.onreadystatechange = () => {
      if (document.readyState == "complete") {
        
        let slideWidth = document.querySelector('.product-images').offsetWidth
        console.log('slideWidth :>> ', slideWidth);
        let draggableSlider = Draggable.create(".container-product-images", {
          type: "x",
          zIndexBoost: false,
          inertia: true,
          snap: {
            x: gsap.utils.snap(slideWidth),
          },
          throwProps: true,
          onClick: function () {
            console.log("clicked");
          },
          onDragEnd: function () {
            console.log("drag ended");
          },
        });
      }
    };
  },
  methods: {
    left() {
      console.log("click");
      gsap.to(this.$refs.productImagesSlider, { duration: 0.6, x: "-=100%", ease: "power4.inOut" });
    },
    right() {
      gsap.to(this.$refs.productImagesSlider, { duration: 0.6, x: "+=100%", ease: "power4.inOut" });
    },
  },
};
</script>

<style scoped>
.preview-main {
  display: flex;
  justify-content: center;
  align-items: center;
  overflow: hidden;
}

.preview-selection {
  display: none;
}

.preview-main .container-product-images {
  display: flex;
  width: 100%;
}

.preview-main .product-images {
  display: block;
  max-width: 100%;
  height: 100%;
}

.preview-main .preview-mobile-selection {
  position: absolute;
  width: 100%;
  display: flex;
  justify-content: space-between;
}

.preview-main .preview-mobile-selection .rounded-button {
  border-radius: 50%;
  background: #fff;
  height: 35px;
  width: 35px;
  display: flex;
  align-items: center;
  justify-content: center;
  margin: 1rem;
  cursor: pointer;
  /* position: absolute; */
}

.preview-main .preview-mobile-selection .rounded-button:first-child svg {
  margin-right: 3px;
}

.preview-main .preview-mobile-selection .rounded-button:last-child svg {
  margin-left: 3px;
}

@media only screen and (min-width: 750px) {
  .preview {
    max-width: 460px;
  }

  .preview .preview-selection {
    margin-top: 2rem;
    display: flex;
    justify-content: space-evenly;
  }

  .preview .preview-selection > div {
    border-radius: 0.75rem;
    cursor: pointer;
    display: flex;
    overflow: hidden;
  }

  .preview .preview-selection > div.active {
    border: solid 3px #e7833b;
  }

  .preview .preview-selection > div.active img {
    opacity: 0.5;
  }

  .preview .preview-selection > div:not(:first-child) {
    margin-left: 1.5rem;
  }

  .preview .preview-selection > div img {
    max-width: 100%;
    /* border-radius: .75rem; */
  }

  .preview-main .preview-mobile-selection {
    display: none;
  }

  .preview-main #preview {
    border-radius: 0.75rem;
  }
}
</style>
