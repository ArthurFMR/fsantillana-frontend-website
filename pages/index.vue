<template>
  <div>
    <Services/>
    <Contact/>
  </div>
</template>

<script>
import Services from "@/components/Services";
import Contact from "@/components/ContactUs";
import FaccebookChat from "@/components/FacebookChat";
import CliengoChat from "@/components/CliengoChat";


export default {
  components: {
    Services,
    Contact,
    FaccebookChat,
    CliengoChat
  },
};
</script>

<style>
</style>
