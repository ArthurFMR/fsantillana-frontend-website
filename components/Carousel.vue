<template>
  <section>
      <b-carousel>
        <b-carousel-item v-for="(slide, index) in slides" :key="index">
            <section>
                    <img :src="slide.img" :alt="slide.title" class="image-slide">
            </section>
        </b-carousel-item>           
    </b-carousel>
  </section>
</template>

<script>
import axios from "axios";
export default {
     data(){
        return {
            slides: []
        }
    },

    created() {
      this.getSlides();
    },
     methods: {
    async getSlides() {
      const server = 'https://fsantillana-api-website.herokuapp.com'
      this.isLoading = true;
      try {
        const url = `${server}/api/v1.0/slides/`;
        const res = await axios.get(url);
        this.slides = res.data;
      } catch (error) {
        console.log(error);
      }
      this.isLoading = false;

    }
  }

}
</script>

<style>

</style>