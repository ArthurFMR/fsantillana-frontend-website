<template>
  <footer class="is-fullwidth inline-block has-text-grey-lighter">
    <div class="columns">
      <div class="column">
        <div>
          <img src="~/assets/imgs/address-icon.png" class="img-icon img-is-white" />
          {{ info.address }}
          <br />
          <img src="~/assets/imgs/phone-icon.png" class="img-icon img-is-white" />
          {{ info.tel }}
          <br />
          <img src="~/assets/imgs/email-icon.png" class="img-icon img-is-white" />
          {{ info.email }}
        </div>
        <div class="has-margin-top-3">
          <a :href="info.facebook" target="_blank" v-if="info.facebook!= ''">
            <img src="~/assets/imgs/facebook-icon.png" class="img-is-white image is-32x32" />
          </a>
          <a :href="info.instagram" target="_blank" v-if="info.instagram!= ''">
            <img src="~/assets/imgs/instagram-icon.png" class="img-is-white image is-32x32" />
          </a>
        </div>
      </div>

      <div class="column">
        <h3 class="title is-4 has-text-grey-lighter">Sobre nosotros</h3>
        <p class="justify-text">{{ info.short_about }}</p>
      </div>

      <div class="column has-margin-left-3">
        <h3 class="title is-4 has-text-grey-lighter">Horario</h3>
        <strong class="has-text-grey-lighter">Lunes-Viernes:</strong>
        {{ info.schedule_monday_friday}}
        <br />
        <strong class="has-text-grey-lighter">Sabado:</strong>
        {{ info.schedule_saturday}}
        <br />
        <strong class="has-text-grey-lighter">Domingo:</strong>
        {{ info.schedule_sunday }}
        <br />
        <strong class="has-text-grey-lighter">Dias Feriados:</strong>
        {{ info.schedule_holidays}}
      </div>
    </div>
    <div class="top-border has-text-centered has-margin-top-3">
      <p>©Copyright 2020, Design and Developed by: Bit_pyr</p>
    </div>
  </footer>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      info: {}
    };
  },
  created() {
    this.getInfo();
  },
  methods: {
    async getInfo() {
        const server = 'https://fsantillana-api-website.herokuapp.com'
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