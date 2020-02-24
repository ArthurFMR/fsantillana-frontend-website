<template>
  <div >
    <NavBar />
    <Carousel />
    <main>
      <nuxt />
    </main>
    <CrispChat/>
    <Footer />
  </div>
</template>
<script>
import NavBar from "@/components/WebNavbar";
import Carousel from "@/components/Carousel";
import Footer from "@/components/Footer";
import WassappChat from "@/components/WhatsappChat";
import CrispChat from "@/components/CrispChat";


export default {
  components: {
    NavBar,
    Carousel,
    Footer,
    CrispChat,
  },

 
};
</script>
<style lang="scss">
@import "~assets/styles/main.scss";
</style>
