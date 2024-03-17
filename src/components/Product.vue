<template>
  <div class="product">
    <div class="container">
      <div class="row">
        <div class="col-md-5 col-xl-6">
          <div class="product__image">
            <img src="../assets/iphone-15.png" alt="">
          </div>
        </div>
        <div class="col-md-7 col-xl-6">
          <div class="product__description">
            <h1 class="title title--big">
              iphone
            </h1>
            <h3 class="title">
              titulo iphone
            </h3>
            <p class="text">
              The innovative new design features back glass that has color infused throughout the material. A custom dual ion-exchange process for the glass, and an aerospace-grade aluminum enclosure, help make iPhone 15 incredibly durable.
            </p>
            <p class="text">
              Condition: new
            </p>
            <p class="text">
              Price: $999
            </p>
            <a
              href="javascript:void(0)"
              data-bs-toggle="modal"
              data-bs-target="#js-modal"
              @click.stop.prevent="showCreditCardModal"
              class="btn">
              Pay with credit card
            </a>
          </div>
        </div>
      </div>
    </div>
  </div>
  <CreditCard />
</template>

<script>
import axios from 'axios';
import $ from 'jquery';

import CreditCard from '../components/CreditCard.vue'

export default {
  components: {
    CreditCard,
  },
  data() {
    return {
      items: [],
      selectedProduct: 'iphone 15',
    }
  },
  methods: {
    showCreditCardModal() {
      $('#js-modal').addClass('show');
      $('#js-modal').show();
      $('body').removeClass('modal-open');
      $('.modal-backdrop').remove();
    },

    // Recreating an API call to select products, but not used because I'm storing the product in the store
    selectProduct() {
      axios
      .get(`https://api.mercadolibre.com/sites/MLA/search?q="${this.selectedProduct}"&&limit=3`)
      .then(response => {
        this.items = response.data.results
        console.log(this.items);
      })
      .catch(error => console.error(error))
    },
  },
  beforeMount() {
    setTimeout(() => {
      this.selectProduct();
    }, 500);
  },
}
</script>

<style lang="scss" scoped>
  @import '../sass/components/product.scss';
</style>