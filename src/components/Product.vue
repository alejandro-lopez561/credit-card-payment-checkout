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
              {{ items[1].attributes[3].value_name }}
            </h1>
            <h3 class="title">
              {{ items[1].title }}
            </h3>
            <p class="text">
              The innovative new design features back glass that has color infused throughout the material. A custom dual ion-exchange process for the glass, and an aerospace-grade aluminum enclosure, help make iPhone 15 incredibly durable.
            </p>
            <p class="text">
              Condition: {{ items[1].condition }}
            </p>
            <p class="text">
              Price: $999
            </p>
            <a @click.prevent="showCreditCardModal"
              class="btn">
              Pay with credit card
            </a>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  data() {
    return {
      items: [],
      selectedProduct: 'iphone 15',
    }
  },
  methods: {
    // Selected a product from a list making an API call to meli api just to mix the ajax call with the storage
    selectProduct() {
      axios
      .get(`https://api.mercadolibre.com/sites/MLA/search?q="${this.selectedProduct}"&&limit=3`)
      .then(response => {
        this.items = response.data.results
        console.log(response.data.results)
      })
      .catch(error => console.error(error))
    },

    showCreditCardModal() {
      // Emit to parent to show credit card modal
      console.log('opening modal');
    }
  },
  beforeMount() {
    this.selectProduct();
  }
}
</script>

<style lang="scss" scoped>
  @import '../sass/components/product.scss';
</style>