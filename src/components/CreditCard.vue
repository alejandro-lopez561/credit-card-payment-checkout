<template>
  <Modal>
    <div class="credit-card">
      <p>Visa</p>
    </div>
  </Modal>
</template>

<script>
import Modal from './Modal.vue';

export default {
  components: {
    Modal,
  }

}
</script>

<style lang="scss" scoped>
  @import '../sass/components/credit-card.scss';
</style>