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
        <div @click="left" ref="leftArrow" class="rounded-button">
          <svg width="12" height="18" xmlns="http://www.w3.org/2000/svg">
            <path d="M11 1 3 9l8 8" stroke="#1D2026" stroke-width="3" fill="none" fill-rule="evenodd" />
          </svg>
        </div>
        <div @click="right" ref="rightArrow" class="rounded-button">
          <svg width="13" height="18" xmlns="http://www.w3.org/2000/svg">
            <path d="m2 1 8 8-8 8" stroke="#1D2026" stroke-width="3" fill="none" fill-rule="evenodd" />
          </svg>
        </div>
      </div>
    </div>
    <div class="preview-selection">
      <div v-for="(listImages, index) in listImages" v-bind:key="index" @click="switchImage(index+1)" :class="[`preview-image-${index+1}`, currentImage === `preview-image-${index+1}` ? 'active': '']">
        <img :src="getImages(this.listImages[index])" alt="Image product 1" />
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
      sliderIndex: 0,
      listImages: [
        'image-product-1-thumbnail.jpg',
        'image-product-2-thumbnail.jpg',
        'image-product-3-thumbnail.jpg',
        'image-product-4-thumbnail.jpg'
      ],
      currentImage : 'preview-image-1'
    };
  },
  mounted() {
    console.log('this.listImages[0] :>> ', this.listImages[0]);

    document.onreadystatechange = () => {
      if (document.readyState == "complete") {
        const self = this;
        let imagesSlider = document.querySelectorAll(".product-images");
        let slideWidth = imagesSlider[0].offsetWidth;
        let totalSliderWidth = document.querySelector(".container-product-images").scrollWidth;
        let xMaxBounds = -(totalSliderWidth - slideWidth);
        gsap.set(self.$refs.leftArrow, { autoAlpha: 0, pointerEvents: "none", ease: "power2.inOut" });

        let draggableSlider = Draggable.create(".container-product-images", {
          type: "x",
          zIndexBoost: false,
          bounds: { minX: 0, maxX: xMaxBounds },
          inertia: true,
          snap: {
            x: gsap.utils.snap(slideWidth),
          },
          throwProps: true,
          onThrowComplete: function (e) {
            if (this.x === 0) gsap.to(self.$refs.leftArrow, { duration: 0.6, autoAlpha: 0, pointerEvents: "none", ease: "power2.inOut" });
            else if (this.x === xMaxBounds) gsap.to(self.$refs.rightArrow, { duration: 0.6, autoAlpha: 0, pointerEvents: "none", ease: "power2.inOut" });
            else gsap.to([self.$refs.rightArrow, self.$refs.leftArrow], { duration: 0.6, autoAlpha: 1, pointerEvents: "all", ease: "power4.inOut" });
          },
        });
      }
    };
  },
  methods: {
    getImages: function (img) {
      return require(`../assets/${img}`)

    },
    switchImage: function (id) {
      this.currentImage = `preview-image-${id}`;
      gsap.to(this.$refs.productImagesSlider, { duration: 0.6, x: `${-(id-1) * 100}%`, ease: "power4.inOut" })
    },
    right(e) {
      this.sliderIndex++;
      console.log("this.sliderIndex :>> ", this.sliderIndex);
      let tlRight = gsap.timeline();
      tlRight
        .set(e.target, { pointerEvents: "none" })
        .to(this.$refs.productImagesSlider, { duration: 0.6, x: "-=100%", ease: "power4.inOut" })
        .set(e.target, { pointerEvents: "all" });

      if (this.sliderIndex >= 3) {
        tlRight.to(e.target, { duration: 0.6, autoAlpha: 0, pointerEvents: "none", ease: "power4.inOut" });
      }
      if (this.sliderIndex !== 0) {
        tlRight.to(this.$refs.leftArrow, { duration: 0.6, autoAlpha: 1, pointerEvents: "all", ease: "power4.inOut" });
      }
    },
    left(e) {
      this.sliderIndex--;
      console.log("this.sliderIndex :>> ", this.sliderIndex);
      let tlLeft = gsap.timeline();
      tlLeft
        .set(e.target, { pointerEvents: "none" })
        .to(this.$refs.productImagesSlider, { duration: 0.6, x: "+=100%", ease: "power4.inOut" })
        .set(e.target, { pointerEvents: "all" });

      if (this.sliderIndex <= 0) {
        tlLeft.to(e.target, { duration: 0.6, autoAlpha: 0, pointerEvents: "none", ease: "power4.inOut" });
      }

      if (this.sliderIndex !== 3) {
        tlLeft.to(this.$refs.rightArrow, { duration: 0.6, autoAlpha: 1, pointerEvents: "all", ease: "power4.inOut" });
      }
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
  border-radius: .75rem;
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

.preview-main .preview-mobile-selection .rounded-button svg {
  pointer-events: none;
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
    outline: solid 3px #e7833b;
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
