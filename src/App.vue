<template>
  <main id="app">
    <Header :quantity="data.length"/>
    <CardList :addQuantity="data.length - 6" />
    <Footer />
    <ScrollToTop />
  </main>
</template>

<script>
import Header from './components/Header.vue'
import CardList from './components/CardList.vue'
import Footer from './components/Footer.vue'
import ScrollToTop from './components/ScrollToTop.vue'
import data from './data.json'
export default {
  data() {
    return {
      data,
    }
  },
  name: 'App',
  components: {
    Header,
    CardList,
    Footer,
    ScrollToTop,
  }
}
</script>

<style>
main {
  padding-bottom: 115px;
}
:root {
  --blue: #64bbd3;
  --black: #1f2021;
  --red: #e62d2d;
  --gray: #f3f3f3;
}
body {
  overflow-x: hidden;
  min-width: 380px;
}
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
#app {
  font-family: 'Montserrat', sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: var(--black);
}
</style>
