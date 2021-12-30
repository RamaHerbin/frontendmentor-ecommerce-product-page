<template>
	<header class="header">
		<div class="wrapper">
			<div class="left">
				<img
					id="burger-menu"
					src="../assets/icon-menu.svg"
					alt="Burger menu icon"
				/>
				<img alt="Sneaker logo" src="../assets/logo.svg" />
				<div class="header-links">
					<a href="#">Collections</a>
					<a href="#">Men</a>
					<a href="#">Women</a>
					<a href="#">About</a>
					<a href="#">Contact</a>
				</div>
			</div>

			<div class="right">
				<div class="cart-wrapper">
					<img id="cartIcon" src="../assets/icon-cart.svg" alt="Cart icon" />
					<div class="nb-cartItem">3</div>
				</div>
				<img class="userPic" src="../assets/image-avatar.png" alt="" />
			</div>
		</div>
	</header>
</template>

<script>
export default {
	name: 'Header',
	mounted: () => {
		console.log(document.querySelectorAll('.wrapper > div'));
	},
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.wrapper {
	display: flex;
	justify-content: space-between;
	align-items: center;
	margin: 0 2rem;
    padding: .5rem;

}

.wrapper #burger-menu {
	margin-right: 1rem;
}

.wrapper .header-links {
	display: none;
	color: hsl(219, 9%, 45%);
}

.wrapper > div {
	display: flex;
	align-items: center;
}

.cart-wrapper {
	display: flex;
	justify-content: center;
}

.right {
	height: 50px;

}

.right .userPic {
	height: 60%;
	margin-left: 1rem;
}

.cart-wrapper .nb-cartItem {
	position: absolute;
}

@media only screen and (min-width: 850px) {
	.header .wrapper {
		border-bottom: solid 1px #e8e8ea;
        padding: 2rem;
		max-width: 1115px;
		margin: 0 auto;
		height: auto;
	}

	.header .wrapper #burger-menu {
		display: none;
	}

	.header .wrapper .header-links {
		display: block;
		margin-left: 2rem;
	}

	.header .wrapper .header-links a {
		padding: 1rem;
		line-height: 1.4;
	}

    .wrapper .right .userPic {
        height: 100%;

    }
}
</style>
