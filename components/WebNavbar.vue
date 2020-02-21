<template>
  <div >
    <header>
      <img :src="info.logo" class="image is-64x64 is-inline-block" alt="Logo" />
      <div class="is-inline-block">
        <h1 class="title">{{ info.company_name }}</h1>
        <h2 class="subtitle">{{ info.subtitle_name }}</h2>
      </div>
      <div class="call-us">
        <img src="~/assets/imgs/phone-icon.png" class="image is-24x24 img-icon" />
        Llámanos: {{ info.tel }}
      </div>
    </header>
    <nav class="is-info navbar is-fixed-top"  role="navigation" aria-label="main navigation">
      <div class="navbar-brand" @click="mobileActive = !mobileActive">
        <a v-if="mobileActive == false"
          role="button"
          class="navbar-burger"
          aria-label="menu"
          aria-expanded="true"
          data-target="navbarBasicExample"
          
        >
          <span aria-hidden="true"></span>
          <span aria-hidden="true"></span>
          <span aria-hidden="true"></span>
        </a>
      </div>
      
     

      <div id="navbarBasicExample" class="navbar-menu" v-bind:class="{'is-active': mobileActive }" >
        <div class="navbar-start">
          <nuxt-link class="navbar-item option" to="/">
          <img src="~/assets/imgs/home-icon.png" class="img-icon-option">Inicio</nuxt-link>
          <nuxt-link class="navbar-item option" to="/#services">
          <img src="~/assets/imgs/services-icon.png" class="img-icon-option">Servicios</nuxt-link>
          <nuxt-link class="navbar-item option" to="/products">
          <img src="~/assets/imgs/products-icon.png" class="img-icon-option">Productos</nuxt-link>
          <nuxt-link class="navbar-item option" to="/#contact">
          <img src="~/assets/imgs/contact-us-icon.png" class="img-icon-option">Contacto</nuxt-link>
          <nuxt-link class="navbar-item option" to="/about">
          <img src="~/assets/imgs/info-icon.png" class="img-icon-option">Sobre Nosotros</nuxt-link>
         
        </div>

        <div class="navbar-end">
          <div class="navbar-item">
           
          </div>
        </div>
      </div>
    </nav>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      mobileActive: false,
      info: {}
    };
  },

  created() {
    this.getInfo();
  },
  methods: {
    async getInfo() {
      const server = "https://fsantillana-api-website.herokuapp.com";
      try {
        const url = `${server}/api/v1.0/companyinfo/`;
        const res = await axios.get(url);
        this.info = res.data[0];
      } catch (error) {
        console.log(error);
      }
    }
  }
};
</script>

<style>
</style>