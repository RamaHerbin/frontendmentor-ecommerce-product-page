<template>
	<div class="product">
        <div class="wrapper">
            <div class="preview">
                <div class="preview-main">
                    <img src="../assets/image-product-1.jpg" alt="Image product" id="preview">
                    <div class="preview-mobile-selection">
                        <div class="rounded-button">
                            <svg width="12" height="18" xmlns="http://www.w3.org/2000/svg">
                                <path d="M11 1 3 9l8 8" stroke="#1D2026" stroke-width="3" fill="none" fill-rule="evenodd"/>
                            </svg>
                        </div>
                        <div class="rounded-button">
                            <svg width="13" height="18" xmlns="http://www.w3.org/2000/svg">
                                <path d="m2 1 8 8-8 8" stroke="#1D2026" stroke-width="3" fill="none" fill-rule="evenodd"/>
                            </svg>
                        </div>
                    </div>
                </div>
                <div class="preview-selection"></div>
            </div>
            <div class="details"></div>
        </div>
	</div>
</template>

<script>
export default {
	name: 'Product',
    mounted: () => {

    }
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
         /* position: absolute; */

    }
/* 
    .preview-main .preview-mobile-selection .rounded-button:first-child {
         left: 15px;

    } */

</style>
