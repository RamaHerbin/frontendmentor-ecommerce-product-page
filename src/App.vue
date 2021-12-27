<template>
  <Header/>
  <Product/>
</template>

<script>
import Header from "@/components/Header";
import Product from "@/components/Product";

export default {
	name: 'App',
  components: {
    Header,
    Product
  }
};
</script>

<style>

html {
  font-size: 100%;
}

* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

a, a:hover, a:focus, a:active {
  text-decoration: none;
  color: inherit;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  max-width: 100%;
}

#nav {
  padding: 30px;
}

#nav a {
  font-weight: bold;
  color: #2c3e50;
}

#nav a.router-link-exact-active {
  color: #42b983;
}
</style>
