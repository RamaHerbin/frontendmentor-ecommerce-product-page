<template>
  <main class="product">
    <div class="wrapper">
      <section class="preview">
        <div class="preview-main">
          <img src="../assets/image-product-1.jpg" alt="Image product" id="preview" />
          <div class="preview-mobile-selection">
            <div class="rounded-button">
              <svg width="12" height="18" xmlns="http://www.w3.org/2000/svg">
                <path d="M11 1 3 9l8 8" stroke="#1D2026" stroke-width="3" fill="none" fill-rule="evenodd" />
              </svg>
            </div>
            <div class="rounded-button">
              <svg width="13" height="18" xmlns="http://www.w3.org/2000/svg">
                <path d="m2 1 8 8-8 8" stroke="#1D2026" stroke-width="3" fill="none" fill-rule="evenodd" />
              </svg>
            </div>
          </div>
        </div>
        <div class="preview-selection"></div>
      </section>
      <section class="details">
        <div class="presentation">
          <div class="product-brand">Sneaker company</div>
          <div class="product-name">Fall Limited Edition Sneakers</div>
          <div class="product-description">
            These low-profiles sneakers are your perfect casual wear companion. Featuring a durable rubber outer sole, they'll withstand everything the weather
            can offer.
          </div>
        </div>
        <div class="price">
          <div class="discount-wrapper">
            <div class="discount-price">$125.00</div>
            <div class="discount-pourcentage">50%</div>
          </div>
          <div class="original-wrapper">$250.00</div>
        </div>
        <div class="cart-section">
          <div class="counter">
            <span class="minus increment">
              <!-- prettier-ignore -->
              <svg width="12" height="4" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink">
                <defs>
                  <path d="M11.357 3.332A.641.641 0 0 0 12 2.69V.643A.641.641 0 0 0 11.357 0H.643A.641.641 0 0 0 0 .643v2.046c0 .357.287.643.643.643h10.714Z" id="a" />
                </defs>
                <use fill="#FF7E1B" fill-rule="nonzero" xlink:href="#a" />
              </svg>
            </span>
            <input type="text" value="1" />
            <span class="plus increment">
              <!-- prettier-ignore -->
              <svg width="12" height="12" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink"><defs><path d="M12 7.023V4.977a.641.641 0 0 0-.643-.643h-3.69V.643A.641.641 0 0 0 7.022 0H4.977a.641.641 0 0 0-.643.643v3.69H.643A.641.641 0 0 0 0 4.978v2.046c0 .356.287.643.643.643h3.69v3.691c0 .356.288.643.644.643h2.046a.641.641 0 0 0 .643-.643v-3.69h3.691A.641.641 0 0 0 12 7.022Z" id="b"/></defs><use fill="#FF7E1B" fill-rule="nonzero" xlink:href="#b"/></svg>
            </span>
          </div>
          <div class="cart-add">
            <svg width="22" height="20" xmlns="http://www.w3.org/2000/svg">
              <path
                d="M20.925 3.641H3.863L3.61.816A.896.896 0 0 0 2.717 0H.897a.896.896 0 1 0 0 1.792h1l1.031 11.483c.073.828.52 1.726 1.291 2.336C2.83 17.385 4.099 20 6.359 20c1.875 0 3.197-1.87 2.554-3.642h4.905c-.642 1.77.677 3.642 2.555 3.642a2.72 2.72 0 0 0 2.717-2.717 2.72 2.72 0 0 0-2.717-2.717H6.365c-.681 0-1.274-.41-1.53-1.009l14.321-.842a.896.896 0 0 0 .817-.677l1.821-7.283a.897.897 0 0 0-.87-1.114ZM6.358 18.208a.926.926 0 0 1 0-1.85.926.926 0 0 1 0 1.85Zm10.015 0a.926.926 0 0 1 0-1.85.926.926 0 0 1 0 1.85Zm2.021-7.243-13.8.81-.57-6.341h15.753l-1.383 5.53Z"
                fill="#ffffff"
                fill-rule="nonzero"
              />
            </svg>
            <span>Add to cart</span>
          </div>
        </div>
      </section>
    </div>
  </main>
</template>

<script>
export default {
  name: "Product",
  mounted: () => {},
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.preview-main {
  display: flex;
  justify-content: center;
  align-items: center;
}

.preview-main #preview {
  max-width: 100%;
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

.details {
  padding: 1.5rem;
}

.presentation .product-brand {
  font-weight: 700;
  text-transform: uppercase;
  color: hsl(26, 100%, 55%);
  letter-spacing: 0.1rem;
  margin-bottom: 0.75rem;
}

.presentation .product-name {
  font-weight: 700;
  font-size: 2.2rem;
  line-height: 1.1;
  margin-bottom: 0.75rem;
}

.presentation .product-description {
  font-weight: 400;
  color: hsl(219, 9%, 45%);
  line-height: 1.5;
  font-size: 1rem;
  margin-bottom: 1.5rem;
}

.price {
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.price .discount-wrapper {
  display: flex;
  align-items: center;
  font-weight: 700;
}

.price .discount-wrapper .discount-price {
  font-size: 1.5rem;
}

.price .discount-wrapper .discount-pourcentage {
  padding: 0.25rem 0.45rem;
  background: hsl(25, 100%, 94%);
  color: hsl(26, 100%, 55%);
  border-radius: 0.3rem;
  margin-left: 0.75rem;
}

.price .original-wrapper {
  color: hsl(219, 9%, 45%);
}

.cart-section {
  margin-top: 1.25rem;
  display: flex;
  flex-direction: column;
}

.cart-section .counter {
  padding: 0.75rem 0.5rem;
  background: hsl(223, 64%, 98%);
  border-radius: 0.5rem;
  display: flex;
  justify-content: space-between;
}

.cart-section .counter .increment {
  display: inline-block;
  height: 100%;
  cursor: pointer;
}

.cart-section .counter .increment:first-child {
  margin-left: 1rem;
}

.cart-section .counter .increment:last-child {
  margin-right: 1rem;
}

.cart-section .counter input {
  border: none;
  text-align: center;
  background-color: inherit;
  font-weight: 700;
  font-size: 1rem;
}

.cart-add {
  margin-top: 0.5rem;
  color: #fff;
  border-radius: 0.75rem;
  background-color: hsl(26, 100%, 55%);
  padding: 1rem;
  font-weight: 700;
  display: flex;
  justify-content: center;
  box-shadow: 0 6px 20px hsla(26, 100%, 55%, 0.55);
  cursor: pointer;
}

.cart-add span {
  margin-left: 0.75rem;
}
</style>
