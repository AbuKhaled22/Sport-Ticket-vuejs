<script>

import home from './components/Home.vue';
import shop from './components/Shop.vue';
import why from './components/Why.vue';
import contact from './components/Contact.vue';
import login from './components/Login.vue';
import cart from './components/Cart.vue';
import { ref } from 'vue';

export default {
  name: 'App',
  components: { 
    home,
    shop,
    why,
    contact,
    login,
    cart
  },
  setup() {
    const page = ref("home");

    const changePage = (pageName) => {
      page.value = pageName;
    }

    return { page, changePage };
  }
}
</script>

<template>
  <div class="body">
    <div class="hero_area">
      <!-- header section strats -->
      <header class="header_section">
        <nav class="navbar navbar-expand-lg custom_nav-container">
          <a class="navbar-brand" href='/' @click="changePage('home')">
            <span>
              Sport Tickets
            </span>
          </a>
          <div class="collapse navbar-collapse innerpage_navbar" id="navbarSupportedContent">
            <ul class="navbar-nav">
              <li class="nav-item">
                <a class="nav-link" href='#' @click="changePage('home')">Home <span class="sr-only">(current)</span></a>
              </li>
              <li class="nav-item">
                <a class="nav-link" href='#' @click="changePage('shop')">
                  Shop
                </a>
              </li>
              <li class="nav-item active">
                <a class="nav-link" href="#" @click="changePage('why')">
                  Why Us
                </a>
              </li>
              <li class="nav-item">
                <a class="nav-link" href='#' @click="changePage('contact')">Contact Us</a>
              </li>
            </ul>
            <div class="user_option">
              <a href="#">
                <i class="bi bi-bag" aria-hidden="true" href="#" @click="changePage('cart')"></i>
              </a>
              <a class="nav-link" href='#' @click="changePage('login')">
                <i class="bi bi-person-circle" aria-hidden="true"></i>
                <span>
                  Login
                </span>
              </a>
            </div>
          </div>
        </nav>
      </header>
      <!-- end header section -->
    </div>

    <div v-if="page === 'shop'">
      <shop />
    </div>
    <div v-else-if="page === 'why'">
      <why />
    </div>
    <div v-else-if="page === 'contact'">
      <contact />
    </div>
    <div v-else-if="page === 'login'">
      <login />
    </div>
    <div v-else-if="page === 'cart'">
      <cart />
    </div>
    <div v-else>
      <home @response="(msg) => page = msg"/>
    </div>
    <div class="info_section  layout_padding2-top">
      <div class="social_container">
        <div class="social_box">
          <a href="https://www.snapchat.com/add/th.abt?share_id=U5lp2HWBhRk&locale=ar-AE">
            <i class="fa fa-facebook" aria-hidden="true"></i>
          </a>
          <a href="https://www.snapchat.com/add/th.abt?share_id=U5lp2HWBhRk&locale=ar-AE">
            <i class="fa fa-twitter" aria-hidden="true"></i>
          </a>
          <a href="https://www.snapchat.com/add/th.abt?share_id=U5lp2HWBhRk&locale=ar-AE">
            <i class="fa fa-instagram" aria-hidden="true"></i>
          </a>
          <a href="https://www.snapchat.com/add/th.abt?share_id=U5lp2HWBhRk&locale=ar-AE">
            <i class="fa fa-youtube" aria-hidden="true"></i>
          </a>
        </div>
      </div>
      <div class="info_container ">
        <div class="container">
          <div class="row">
            <div class="col-md-6 col-lg-3">
              <h6>
                ABOUT US
              </h6>
              <p>
                Sport Ticket is your premier destination for securing tickets to the hottest sports events worldwide. 
              </p>
            </div>
            <div class="col-md-6 col-lg-3">
              <div class="info_form ">
                <h5>
                  Newsletter
                </h5>
                <form action="#">
                  <input type="email" placeholder="Enter your email"/>
                  <button>
                    Subscribe
                  </button>
                </form>
              </div>
            </div>
            <div class="col-md-6 col-lg-3">
              <h6>
                NEED HELP
              </h6>
              <p>
                Our dedicated support team is here to help. Contact us anytime for a winning experience!
              </p>
            </div>
            <div class="col-md-6 col-lg-3">
              <h6>
                CONTACT US
              </h6>
              <div class="info_link-box">
                <a href="">
                  <i class="fa fa-map-marker" aria-hidden="true"></i>
                  <span> Gb road 123 london Uk </span>
                </a>
                <a href="">
                  <i class="fa fa-phone" aria-hidden="true"></i>
                  <span>+60 12345678901</span>
                </a>
                <a href="">
                  <i class="fa fa-envelope" aria-hidden="true"></i>
                  <span> kingboyabood@gmail.com</span>
                </a>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
  
</template>


<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.body {
  font-family: "poppins", sans-serif;
  background-color: #d2e9d1;
}

.layout_padding {
  padding-top: 90px;
  padding-bottom: 90px;
}

.layout_padding2-top {
  padding-top: 45px;
}

.heading_container {
  display: -webkit-box;
  display: -ms-flexbox;
  display: flex;
  -webkit-box-orient: vertical;
  -webkit-box-direction: normal;
      -ms-flex-direction: column;
          flex-direction: column;
}

.heading_container h2 {
  text-transform: uppercase;
  font-weight: bold;
}


.heading_container.heading_center {
  -webkit-box-align: center;
      -ms-flex-align: center;
          align-items: center;
  text-align: center;
}

.hero_area {
  padding: 0 45px;
}

#navbarSupportedContent {
  width: 100%;
  -webkit-box-pack: center;
      -ms-flex-pack: center;
          justify-content: center;
  padding: 10px 0;
  border-radius: 15px 15px 0 0;
  font-size: 25px;
  font-weight: bold;
}

#navbarSupportedContent.innerpage_navbar {
  background-color: rgb(180, 237, 209);
  border-radius: 10px;
  -webkit-box-shadow: 0 0 3px 0 rgba(0, 0, 0, 0.25);
          box-shadow: 0 0 3px 0 rgba(0, 0, 0, 0.25);
}

#navbarSupportedContent.innerpage_navbar .nav-item.active .nav-link {
  background-color: #f4f5f6;
}

#navbarSupportedContent .navbar-nav .nav-link {
  padding: 5px 25px;
  color: #514f4f;
  text-align: center;
  text-transform: uppercase;
  border-radius: 5px;
}

#navbarSupportedContent .nav-item.active .nav-link {
  background-color: #ffffff;
}

a,
a:hover,
a:focus {
  text-decoration: none;
}

a:hover,
a:focus {
  color: initial;
}

.btn,
.btn:focus {
  outline: none !important;
  -webkit-box-shadow: none;
          box-shadow: none;
}

.navbar-brand {
  margin: 15px 0;
  padding: 0;
}

.navbar-brand span {
  font-size: 28px;
  font-weight: bold;
  color: #000000;
  text-transform: uppercase;
  margin: 0;
  padding: 0;
}

.custom_nav-container .nav_search-btn {
  padding: 0;
  border: none;
}

.custom_nav-container {
  z-index: 99999;
  padding: 0;
  -webkit-box-orient: vertical;
  -webkit-box-direction: normal;
      -ms-flex-direction: column;
          flex-direction: column;
  -webkit-box-align: center;
      -ms-flex-align: center;
          align-items: center;
}
.user_option {
  display: -webkit-box;
  display: -ms-flexbox;
  display: flex;
  -webkit-box-align: center;
      -ms-flex-align: center;
          align-items: center;
  margin-left: 25px;
}

.user_option a {
  margin-right: 25px;
  color: #000000;
}

.user_option a span {
  margin-left: 5px;
}

/* info section */
.info_section {
  position: relative;
  background-color: #295629;
  color: #ffffff;
  margin: 0 45px 45px;
}

.info_section .social_container {
  -webkit-box-pack: center;
      -ms-flex-pack: center;
          justify-content: center;
  margin-top: 25px;
  margin-bottom: 30px;
}

.info_section .social_container .social_box {
  display: -webkit-box;
  display: -ms-flexbox;
  display: flex;
  -webkit-box-align: center;
      -ms-flex-align: center;
          align-items: center;
  -webkit-box-pack: center;
      -ms-flex-pack: center;
          justify-content: center;
}

.info_section .social_container .social_box a {
  margin: 0 10px;
  color: #ffffff;
  font-size: 24px;
}

.info_section .info_form form input {
  outline: none;
  width: 100%;
  padding: 7px 10px;
}

.info_section .info_form form button {
  padding: 8px 35px;
  outline: none;
  border: none;
  color: #ffffff;
  background: #f89cab;
  margin-top: 15px;
  text-transform: uppercase;
}

.info_section .row > div {
  margin-top: 25px;
}

.info_section a {
  text-transform: none;
}

.info_section h6 {
  font-weight: bold;
  text-transform: uppercase;
  font-size: 18px;
  margin-bottom: 25px;
}

.info_section p {
  color: #cbc9c9;
}

.info_section .info_link-box a {
  display: -webkit-box;
  display: -ms-flexbox;
  display: flex;
  -webkit-box-align: center;
      -ms-flex-align: center;
          align-items: center;
  margin: 15px 0;
}

.info_section .info_link-box a:hover {
  color: #ffffff;
}

.info_section .info_link-box a i {
  color: #ffffff;
  margin-right: 5px;
  font-size: 18px;
}

.info_section .info_link-box a span {
  color: #cbc9c9;
}

.info_section .info_link-box a:hover span {
  color: #ffffff;
}

/* end info section */

/* footer section*/
.footer_section {
  margin-top: 45px;
  font-weight: 500;
}

.footer_section p {
  padding: 20px 0;
  margin: 0 auto;
  text-align: center;
  border-top: 1.5px solid #eeeeee;
  width: 80%;
}

.footer_section a {
  color: #cbc9c9;
}

/* end footer section*/

</style>
