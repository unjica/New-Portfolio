<template>
  <Nav />
  <router-view class="min-height"/>
  <Footer />
</template>

<script>
import Nav from './components/Nav'
import Footer from './components/Footer'

export default {
  name: 'App',
  components: {
    Nav,
    Footer
  }
}
</script>

<style lang="scss">
@import './styles/_variables.scss';

@font-face {
  font-family: Luxia;
  src: url("./fonts/Luxia-Regular.otf");
}

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
#app {
  font-family: Luxia, Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  font-size: 20px;
  color: $dark-color;
  background-color: $light-color;
}
.wrapper {
  width: 100%;
  max-width: 1536px;
  margin: auto;
}
.min-height {
  min-height: 100vh;
}
</style>
