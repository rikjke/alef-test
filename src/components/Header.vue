<template>
  <header class="header">
    <div class="header__inner">
      <Hamburger/>
          <div class="navbar">
            <img src="../assets/logo.svg" alt="logo brand">
            <ul class="header__menu">
              <li class="header__item">
                <a href="#" class="header__link">Main</a>
              </li>
              <li class="header__item">
                <a href="#" class="header__link">Gallery</a>
              </li>
              <li class="header__item">
                <a href="#" class="header__link">News</a>
              </li>
              <li class="header__item">
                <a href="#" class="header__link">Profile</a>
              </li>
            </ul>

            <div class="contacts">
              <div class="contacts__number">+544 3490 00000</div>
              <div class="contacts__description">Звони скорее!</div>
            </div>

          </div>
          <h1 class="found">Найдено {{quantity}} котов</h1>
    </div>
  </header>
</template>

<script>
import Hamburger from './Hamburger.vue'
export default {
  name: 'Header',
  data() {
    return {
      active: false,
    }
  },
  props: {
    quantity: {
      type: Number,
    },
  },
  components: {
    Hamburger,
  },
}
</script>

<style>
.header__inner {
  max-width: 1280px;
  margin: 0 auto;
}
.navbar {
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin-bottom: 50px;
  transition: .4s ease
}
.header__menu {
  list-style-type: none;
  display: flex;
}
.header__item {
  margin-right: 45px;
}
.header__item:last-child {
  margin-right: 0px;
}
.header__link {
  color: #fff;
  text-decoration: none;
  text-transform: capitalize;
  position: relative;
}
.header__link::after {
  position: absolute;
  content: '';
  width: 100%;
  height: 1px;
  bottom: 0;
  left: 0;
  background-color: #fff;
  transition: 0.4s ease all;
  transform: scale(0)
}
.header__link:hover::after{
  transform: scale(1)
}
.header {
  min-height: 252px;
  padding: 40px 0 66px;
  background: url('../assets/header-bg.svg') center bottom no-repeat, rgba(0,0,0, .25);
  background-size: cover;
  z-index: 1;
  color: #fff;
  position: relative;
}
.header::after {
  content: '';
  position: absolute;
  left: 0;
  right: 0;
  top: 0;
  bottom: 0;
  background: rgba(31, 32, 33, 0.79);
  z-index: -2;
}
.contacts {
  text-align: right;
}
.contacts__number {
  font-weight: 700;
  font-size: 24px;
}
@media screen and (max-width: 780px) {
  .navbar {
    position: fixed;
    background-color: rgba(0,0,0,.75);
    padding: 75px;
    top: 0;
    height: 100vh;
    bottom: 0;
    left: 0;
    right: 0;
    flex-direction: column;
    align-items: flex-start;
    justify-content: space-between;
  }
  .navbar ul {
    flex-direction: column;
  }
  .navbar a {
    font-size: 45px;
  }
}
</style>
