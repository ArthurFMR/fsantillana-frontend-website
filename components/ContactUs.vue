<template>
  <section id="contact" class="container sections">
    <h1 class="title is-2 has-text-centered">Contáctanos</h1>

    <div class="columns">
      <div class="column is-full">
        <div class="contacts-info">
          <img src="~/assets/imgs/address-icon.png" class="img-icon" />
          {{ info.address }}
          <br />
          <img src="~/assets/imgs/whatsapp-blue.png" class="img-icon image is-24x24" />
          +{{ info.whatsapp }}
          <br />
          <img src="~/assets/imgs/phone-icon.png" class="img-icon" />
          {{ info.tel }}
          <br />
          <img src="~/assets/imgs/email-icon.png" class="img-icon" />
          {{ info.email }}
        </div>
        <progress v-if="isLoading" class="progress is-small is-info" max="100"></progress>
        <iframe
          :src="info.src_googlemap"
          width="100%"
          height="450"
          frameborder="0"
          style="border:0;"
          allowfullscreen
        ></iframe>
      </div>
    </div>
  </section>
</template>

<script>
import axios from "axios";
export default {
    data() {
      return {
        isLoading: false,
        info: {}
      };
    },
    created() {
      this.getInfo();
    },
     methods: {
    async getInfo() {
      this.isLoading = true;
      const server = 'https://fsantillana-api-website.herokuapp.com'
      try {
        const url = `${server}/api/v1.0/companyinfo/`;
        const res = await axios.get(url);
        this.info = res.data[0];
      } catch (error) {
        console.log(error);
      }
      this.isLoading = false;

    }
  }
};
</script>

<style>
</style>