<template>
  <div>
    <!-- Load Facebook SDK for JavaScript -->
    <div id="fb-root"></div>

    <!-- Your customer chat code -->
    <div class="fb-customerchat" attribution="setup_tool" page_id="108078170786103"></div>
  </div>
</template>

<script>
export default {
  created() {
    return (function(d, s, id) {
      var js,
        fjs = d.getElementsByTagName(s)[0];
      if (d.getElementById(id)) return;
      js = d.createElement(s);
      js.id = id;
      js.src = "https://connect.facebook.net/en_US/sdk/xfbml.customerchat.js";
      fjs.parentNode.insertBefore(js, fjs);
    })(document, "script", "facebook-jssdk");
  },

  mounted() {
    window.fbAsyncInit = function() {
      FB.init({
        xfbml: true,
        version: "v6.0"
      });
    };
  }
};
</script>

<style>
</style>