<template>
  <div >
    <NavBar />
    <Carousel />
    <main>
      <nuxt />
      <FaccebookChat/>
      <CliengoChat/>
    </main>
    <Footer />
  </div>
</template>
<script>
import NavBar from "@/components/WebNavbar";
import Carousel from "@/components/Carousel";
import Footer from "@/components/Footer";
import WassappChat from "@/components/WhatsappChat";
import FaccebookChat from "@/components/FacebookChat";
import CliengoChat from "@/components/CliengoChat";

export default {
  components: {
    NavBar,
    Carousel,
    Footer,
    WassappChat,
    FaccebookChat,
    CliengoChat
  },

 
};
</script>
<style lang="scss">
@import "~assets/styles/main.scss";
</style>
