<template>
  <div class="container has-margin-bottom-2">
    <div class="columns">
      <div class="column is-three-fifths">
        <h1 class="title is-3 has-margin-top-1">Sobre Nosotros</h1>
        <p class="justify-text">{{ info.about }}</p>
      </div>
      <div class="columns">
        <img :src="info.building_img" class="has-margin-top-3 has-margin-left-1" />
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
import CrispChat from "@/components/CrispChat";
export default {
  components:{
  },
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