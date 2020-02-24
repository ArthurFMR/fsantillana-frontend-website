<template>
  <div>
    <NavBar />
    <Carousel />
    <main>
      <nuxt />
    </main>
    <messanger />
    <Footer />
  </div>
</template>
<script>
import NavBar from "@/components/WebNavbar";
import Carousel from "@/components/Carousel";
import Footer from "@/components/Footer";
import messanger from "@/components/FacebookChat";

export default {
  components: {
    NavBar,
    Carousel,
    Footer,
    messanger
  }
};
</script>
<style lang="scss">
@import "~assets/styles/main.scss";
</style>
