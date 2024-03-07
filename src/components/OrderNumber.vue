<template>
  <div>
    <h3>{{ orderNumberInfo }}</h3>
  </div>
</template>
<script>
export default {
  props: {
    orderNumber: String
  },
  computed: {
    orderNumberInfo() {
      if (!this.orderNumber) {
        return 'No order selected';
      }
      return `Order Number :${this.orderNumber}`;
    }
  }
};
</script>
<style scoped></style>
