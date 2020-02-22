<template>
  <div class="container has-margin-top-2 has-margin-bottom-2 clearfix">
    <progress v-if="isLoading" class="progress is-small is-info" max="100"></progress>
    <aside>
      <input
        v-model="search"
        class="input is-rounded is-primary has-margin-bottom-2"
        type="text"
        placeholder="Buscar Producto"
      />
      <div class="has-background-info has-padding-bottom-1 has-padding-top-1 has-padding-left-1">
        <img src="~/assets/imgs/sorting-icon.png" class="img-icon img-is-white" />
        <h4 class="title is-4 has-text-white">Categorias</h4>
      </div>
      <div class="field has-margin-top-1">
        <b-radio v-model="selectedCategory" native-value="all" class="has-margin-bottom-1">Todos</b-radio>
        <br />
        <b-radio
          v-model="selectedCategory"
          native-value="office"
          class="has-margin-bottom-1"
        >Oficina</b-radio>
        <br />
        <b-radio
          v-model="selectedCategory"
          native-value="school"
          class="has-margin-bottom-1"
        >Escolar</b-radio>
        <br />
        <b-radio
          v-model="selectedCategory"
          native-value="cel_accessory"
          class="has-margin-bottom-1"
        >Accesorios para celulares</b-radio>
        <br />
        <button class="button is-white" @click="isActive = !isActive">
          Computadoras (PC)
          <img src="~/assets/imgs/up-icon.png" v-if="isActive == false" />
          <img src="~/assets/imgs/down-icon.png" v-if="isActive == true" />
        </button>
        <ul v-if="isActive!=false">
          <li>
            <b-radio
              v-model="selectedCategory"
              native-value="desktop"
              class="has-margin-bottom-1"
            >Computadoras de Escritorio</b-radio>
          </li>
          <li>
            <b-radio
              v-model="selectedCategory"
              native-value="laptops"
              class="has-margin-bottom-1"
            >Laptops</b-radio>
          </li>
          <li>
            <b-radio
              v-model="selectedCategory"
              native-value="pc_accessory"
              class="has-margin-bottom-1"
            >Accesorios para PC</b-radio>
          </li>
          <li>
            <b-radio
              v-model="selectedCategory"
              native-value="pc_components"
              class="has-margin-bottom-1"
            >Piezas para Computadoras</b-radio>
          </li>
        </ul>
      </div>
    </aside>

    <div class="columns is-multiline">
      <div
        class="column is-one-third has-margin-bottom-3"
        v-for="(product, index) in filterProduct"
        :key="index"
      >
        <div class="card">
          <div class="card-image">
            <figure class="image is-4by3 is-relative">
              <span v-if="product.old_price" class="tag is-danger offer-tag">Oferta</span>
              <img :src="product.img" alt="Placeholder image" />
            </figure>
          </div>
          <div class="card-content">
            <div class="media">
              <div class="media-content">
                <p class="title is-4 has-text-info">{{ product.name }}</p>
              </div>
            </div>

            <div class="content">
              <p>{{ product.description }}</p>

              <br />
              <span class="tag is-success has-margin-right-1">{{ currencyFormat(product.price) }}</span>
              <span
                v-if="product.old_price"
                class="tag is-light text-line-through"
              >{{ currencyFormat( product.old_price) }}</span>
            </div>
          </div>
        </div>
      </div>
    </div>

     <!-- Load Facebook SDK for JavaScript -->
    <div id="fb-root"></div>
    <script>
  window.fbAsyncInit = function() {
    FB.init({
      xfbml: true,
      version: "v6.0"
    });
  };

  (function(d, s, id) {
    var js,
      fjs = d.getElementsByTagName(s)[0];
    if (d.getElementById(id)) return;
    js = d.createElement(s);
    js.id = id;
    js.src = "https://connect.facebook.net/en_US/sdk/xfbml.customerchat.js";
    fjs.parentNode.insertBefore(js, fjs);
  })(document, "script", "facebook-jssdk");
    </script>

    <!-- Your customer chat code -->
    <div class="fb-customerchat" attribution="setup_tool" page_id="108078170786103"></div>
    
  </div>
</template>

<script>
import axios from "axios";
export default {
  components:{
  },
  data() {
    return {
      isLoading: false,
      isActive: false,
      selectedCategory: "all",
      search: "",
      products: []
    };
  },

  computed: {
    filterProduct() {
      const search = this.search.toLowerCase();

      return this.products.filter(product => {
        const name = product.name.toLowerCase();
        const category = product.category;

        if (this.selectedCategory != "all") {
          return category.match(this.selectedCategory);
        } else {
          return name.match(search);
        }
      });
    }
  },

  watch: {
    search: function() {
      this.selectedCategory = "all";
    }
  },

  created() {
    this.getProducts();
  },

  methods: {
    async getProducts() {
      const server = "https://fsantillana-api-website.herokuapp.com";
      try {
        this.isLoading = true;
        const url = `${server}/api/v1.0/products/`;
        const rest = await axios.get(url);
        this.products = rest.data;
        this.isLoading = false;
      } catch (error) {
        console.log(error);
      }
    },
    currencyFormat(number) {
      return (
        "RD$ " + number.toFixed(2).replace(/(\d)(?=(\d{3})+(?!\d))/g, "$1,")
      );
    }
  }
};
</script>

<style>
</style>