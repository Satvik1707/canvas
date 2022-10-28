<template>
  <div class="container">
    <div class="logo">
      <p>AVYUKT WORLD</p>
      <div class="menu" v-on:click="navbar_open">
        <div class="menu-item"></div>
        <div class="menu-item"></div>
        <div class="menu-item"></div>
      </div>
    </div>
    <ul class="navbar" ref="navbar">
      <li class="nav-list">
        <router-link to="/"> Home </router-link>
      </li>
      <li class="nav-list">
        <router-link to="/"> About </router-link>
      </li>
      <li class="nav-list">
        <router-link to="/"> My Works </router-link>
      </li>
      <li class="nav-list">
        <router-link to="/shop">Shop Now</router-link>
      </li>
      <li>
        <a href="">
          <button class="contact-us">Contact Us</button>
        </a>
      </li>
    </ul>
  </div>
</template>

<style lang="css" scoped>
*,
html {
  margin: 0;
  padding: 0;
  /* border: 1px solid red; */
}

.logo {
  font-family: Poppins, sans-serif;
  font-weight: 300;
  white-space: nowrap;
}

.container {
  padding: 1em 5em 1em 5em;
  display: flex;
  flex-direction: row;
  justify-content: space-around;
  align-items: center;
  border-bottom: 1px solid black;
}

.logo {
  display: flex;
  font-size: 24px;
}

.navbar {
  display: flex;
  justify-items: center;
  align-items: center;
  list-style: none;
  margin: 0;
}

.nav-list {
  margin: 1.5em;
  align-items: center;
}

.nav-list a {
  text-decoration: none;
  display: block;
  color: #1c1c1d;
  font-family: 'Poppins', sans-serif;
  font-weight: 400;
  font-size: 16px;
}

.nav-list a::after {
  content: '';
  display: block;
  width: 0;
  height: 1.5px;
  background: #000;
  transition: width 1s;
}

.nav-list a:is(.router-link-exact-active)::after {
  content: '';
  display: block;
  width: 100%;
  height: 1.5px;
  background: #000;
  transition: width 1s;
}

.nav-list a:hover::after {
  width: 100%;
  transition: width 0.3s;
}

/* .navigation li a.router-link-exact-active{
  font-weight: 550;
} */

/* .contact-us {
  width: 130px;
  height: 40px;
  background: #f8f8f8;
  border: 0.5px solid #1c1c1d;
  font-weight: 700;
  border-radius: 30px;
  -webkit-box-shadow: 0px 0px 24px -10px rgba(0, 0, 0, 0.75);
  -moz-box-shadow: 0px 0px 24px -10px rgba(0, 0, 0, 0.75);
  box-shadow: 0px 0px 24px -11px rgba(0, 0, 0, 0.75);
  cursor: pointer;
} */

.contact-us {
  width: 140px;
  height: 50px;
  border: none;
  outline: none;
  color: #fff;
  font-family: Poppins, sans-serif;
  font-weight: 700;
  background: #111;
  cursor: pointer;
  position: relative;
  z-index: 0;
  border-radius: 25px;
  margin-left: 20px;
}

.contact-us:before {
  content: '';
  background: linear-gradient(
    45deg,
    #ff0000,
    #ff7300,
    #fffb00,
    #48ff00,
    #00ffd5,
    #002bff,
    #7a00ff,
    #ff00c8,
    #ff0000
  );
  position: absolute;
  top: -2px;
  left: -2px;
  background-size: 400%;
  z-index: -1;
  filter: blur(5px);
  width: calc(100% + 4px);
  height: calc(100% + 4px);
  animation: glowing 20s linear infinite;
  opacity: 0;
  transition: opacity 0.3s ease-in-out;
  border-radius: 25px;
}

.contact-us:active {
  color: #000;
}

.contact-us:active:after {
  background: transparent;
}

.contact-us:hover:before {
  opacity: 1;
}

.contact-us:after {
  z-index: -1;
  content: '';
  position: absolute;
  width: 100%;
  height: 100%;
  background: #111;
  left: 0;
  top: 0;
  border-radius: 25px;
}

@keyframes glowing {
  0% {
    background-position: 0 0;
  }
  50% {
    background-position: 400% 0;
  }
  100% {
    background-position: 0 0;
  }
}

.menu {
  display: none;
}

.menu:hover {
  cursor: pointer;
}

.menu-item {
  width: 20px;
  height: 3px;
  background-color: #1c1c1d;
  margin-bottom: 3px;
}

@media (max-width: 575.98px) {
}

/* Small devices (landscape phones, less than 768px) */
@media (max-width: 767.98px) {
}

/* // Medium devices (tablets, less than 992px) */
@media (max-width: 991.98px) {
}
/* // Large devices (desktops, less than 1200px) */
@media (max-width: 1199.98px) {
}

@media (max-width: 1035.98px) {
  .container {
    flex-direction: column;
    padding: 1em 10% 1em 15%;
  }

  .logo {
    display: flex;
    align-items: center;
    width: 100%;
    text-align: center;
    justify-content: center;
    align-content: center;
    justify-content: space-between;
    font-size: 24px;
  }

  .navbar {
    flex-direction: column;
    display: block;
  }
  .nav-list {
    padding: 0;
    margin: 15px 0 15px 0;
    text-align: center;
  }
  .menu {
    display: block;
  }
  .navbar {
    display: none;
  }
  .active {
    display: block;
  }
  .contact-us {
    margin-left: 0;
  }
}
</style>

<script>
export default {
  methods: {
    navbar_open: function() {
      this.$refs.navbar.classList.toggle('active')
    }
  }
}
</script>
