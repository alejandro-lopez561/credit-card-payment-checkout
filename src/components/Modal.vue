<template>
  <div class="modal fade show" id="js-modal" tabindex="-1" role="dialog" ref="modal">
    <div class="modal-dialog modal-dialog-centered" role="document">
      <button class="hamburger--collapse is-active close"
        type="button"
        data-dismiss="modal"
        aria-label="Close"
        @click="$emit('close-modal')">
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
  emits: ['close-modal'],
  mounted() {
    $('#js-modal').show();
  }
};
</script>

<style lang="scss" scoped>
  @import '../sass/components/modal.scss';
</style>
