<template>
  <div class="modal fade show" id="js-modal" data-bs-backdrop="static" data-bs-keyboard="false" tabindex="-1" aria-labelledby="modal-js" aria-hidden="true">
    <div class="modal-dialog modal-dialog-centered" role="document">
      <button class="hamburger--collapse is-active close"
        type="button"
        data-bs-dismiss="modal"
        aria-label="Close"
        @click.prevent="closeModal">
        <span class="hamburger-box">
          <span class="hamburger-inner"></span>
        </span>
      </button>

      <div class="modal-content">
        <div class="container">
          <div>
            <slot></slot>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import $ from 'jquery';

export default {
  methods: {
    closeModal() {
      $('#js-modal').hide();
      $('body').removeClass('modal-open');
      $('.modal-backdrop').remove();
    }
  },
};
</script>

<style lang="scss" scoped>
  @import '../sass/components/modal.scss';
</style>
