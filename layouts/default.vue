<template>
  <div >
    <NavBar />
    <Carousel />
    <main>
      <nuxt />
        <WassappChat/>
    </main>
    <Footer />
  </div>
</template>
<script>
import NavBar from "@/components/WebNavbar";
import Carousel from "@/components/Carousel";
import Footer from "@/components/Footer";
import WassappChat from "@/components/WhatsappChat";

export default {
  components: {
    NavBar,
    Carousel,
    Footer,
    WassappChat
  },

 
};
</script>
<style lang="scss">
@import "~assets/styles/main.scss";
</style>
