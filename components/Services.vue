<template>
  <section id="services" class="sections">
      <div class="container">
    <h1 class="has-text-centered is-size-2 has-margin-bottom-1">Nuestros <strong>Servicios</strong></h1>
    <div class="columns is-multiline">
      <progress v-if="isLoading" class="progress is-small is-info" max="100"></progress>
      <div class="column is-one-quarter" v-for="(service, index) in services" :key="index">
        <div class="content-service">
          <div class="is-flex is-horizontal-center">
            <figure class="image is-128x128">
              <img :src="service.img" :alt="service.title" />
            </figure>
          </div>
          <div>

            <p class="title is-4 has-text-centered">{{ service.title }}</p>

            <div class="justify-text">
              {{ service.description }}
            </div>
          </div>
        </div>
      </div>
    </div>
    </div>
  </section>
</template>

<script>
import axios from 'axios'

export default {
  data() {
    return {
        isLoading:false,
        services: []
    }
  },

  created(){
      this.getServices()
  },

  methods:{
   async getServices(){
     const server = 'https://fsantillana-api-website.herokuapp.com'
     try {
       this.isLoading = true;
       const url = `${server}/api/v1.0/services/`;
        const res = await axios.get(url);
        this.services = res.data;
        this.isLoading = false;
       
     } catch (error) {
       console.log(error)

     }
     
    }
  }
};
</script>

<style>
</style>