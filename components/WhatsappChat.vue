<template>
  <div>
    <transition name="fade">
    <div class="chat-popup" v-if="activeChat">
      <img @click="activeChat=!activeChat" class="image is-32x32 pointer" src="~/assets/imgs/close.png" /> 
    <div class="card">
      
      <div class="card-header">
        <figure class="image is-64x64 has-margin-left-1 has-margin-top-1 has-margin-bottom-1">
          <img class="is-rounded" src="~/assets/imgs/logo.jpg" /> 
        </figure>
       
        <p class="card-header-title has-text-white">FSantillana</p>
  
      </div>
             

        <div class="msg has-margin-top-1 has-margin-bottom-1">
          <div class="bubble">
            <div class="txt">
              <span class="message">¿En que podriamos ayudarle?</span>
            </div>
            <div class="bubble-arrow"></div>
          </div>
        </div>
   
      <div class="has-margin-bottom-1 has-margin-left-1 has-margin-right-1 ">
        <input v-model="message" class="has-padding-left-1 has-margin-bottom-1" type="text" placeholder="Escribenos un messaje" />
        <a @click="replaceSpaces" target="_blank" :href="'https://wa.me/8298910424?text=' + message">
        <img src="~/assets/imgs/send.png" width="15%" align="right"/>
        </a>
      </div>
    </div>
    </div>
    </transition>
      <img @click="activeChat=!activeChat" class="image is-64x64 whatsapp-button pointer" src="~/assets/imgs/whatsapp.png" />
  </div>
</template>

<script>
export default {
  components: {},
  data() {
    return {
      activeChat: false,
      message:'',
    };
  },

  methods:{
    replaceSpaces(){
      this.message = this.message.replace(" ", "%20");
    }
  }
};
</script>

<style lang="scss" scoped>
/* Button used to open the chat form - fixed at the bottom of the page */
.whatsapp-button {
  position: fixed;
  right: 26px;
  bottom: 100px;
  z-index: 1000;
}

.pointer {cursor: pointer;}

.card-header {
  background-color: #0d6652;
}

input {
  border-radius: 25px;
  border: none;
  width: 85%;
  outline: none;
  height: 30px;
 
}

.card{
  background-image: url("../assets/imgs/wallpaper-whatsapp.png");
}


.chat-popup {
  position: fixed;
  right: 57px;
  bottom: 160px;
  z-index: 1000;
  width: 25%;
  

}

@media screen and (max-width: 360px) {

  .chat-popup {
    width: 80%; 
  }

}

.msg{
  width:100%;
  height:auto;
  display:block;
  overflow:hidden;
    
  .bubble{
    float:left;
    max-width: 75%;
    width: auto;    
    height: auto;
    display: block;
    background: #ebebeb;
    border-radius: 5px;
    position: relative;
    margin: 10px 0 3px 25px;   
    box-shadow: 0px 2px 1px rgba(0, 0, 0, 0.2);
    
    &.alt{
      margin: 10px 25px 3px 0px;
      background:#DCF8C6;
      float:right;
    }
    &.follow{
      margin: 2px 0 3px 25px;
    }
    
    &.altfollow{
      margin: 2px 25px 3px 0px;
      background:#DCF8C6;
      float:right;   
    }
    .txt{
      padding: 8px 0 8px 0;
      width:100%;
      
      .message{
        font-size: 14px;
        font-weight:500;
        padding: 0 15px 0 15px;
        margin: auto;
        color: #2b2b2b;
        display: table;
      }
     
    }
    .bubble-arrow {
      position: absolute;
      float:left;
      left: -11px;
      top: 0px;
      &.alt{
        bottom: 20px;
        left: auto;
        right: 4px;
        float:right;
      }
    }
    .bubble-arrow:after {
      content: "";
      position: absolute;
      border-top: 15px solid #ebebeb;
      border-left: 15px solid transparent;           
      border-radius: 4px 0 0 0px;
      width: 0;
      height: 0;
      //box-shadow: 0px 0px 2px rgba(0, 0, 0, 0.2); 
      //looks like I can't give a shadow to the arrows
    }
    .bubble-arrow.alt:after {
      border-top: 15px solid #DCF8C6;
      transform: scaleX(-1);
    }
  }
}
</style>