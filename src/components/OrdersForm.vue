<template>
  <div>
    <h3>Add new product to the order:</h3>

    <div class="form-container card">
      <form @submit.prevent="addOrder()">
        <div>
          <label for="skue">SKU: </label>
          <input required type="text" v-model="formOrder.sku" />
        </div>

        <div>
          <label for="skue">Name: </label>
          <input required type="text" v-model="formOrder.name" />
        </div>
        <div>
          <label for="skue">Quantity: </label>
          <input required type="number" v-model="formOrder.quantity" />
        </div>
        <div>
          <label for="skue">Price: </label>
          <input required type="number" v-model="formOrder.price" />
        </div>
        <input class="add-button" type="submit" value="Add Product" />
      </form>
    </div>
  </div>
</template>
<script>
export default {
  props: {
    orders: Array
  },
  data: () => {
    return {
      formOrder: {
        sku: '',
        name: '',
        quantity: '',
        price: ''
      }
    };
  },
  methods: {
    addOrder() {
      this.$emit('newOrder', this.formOrder);
      this.formOrder = {
        sku: '',
        name: '',
        quantity: '',
        price: ''
      };
    }
  }
};
</script>
<style scoped>
.card {
  box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2);
  transition: 0.3s;
}

.card:hover {
  box-shadow: 0 8px 16px 0 rgba(0, 0, 0, 0.2);
}
.form-container {
  border: 2px solid gray;
  padding: 10px;
  margin: 20px 0;
  width: 350px;
}
.add-button {
  margin-top: 10px;
  padding: 6px;
  border-radius: 8px;
  border: gray;
  color: black;
}
.add-button:hover {
  background: gray;
  color: beige;
}
div label {
  display: inline-block;
  width: 70px;
  text-align: right;
  padding-right: 10px;
  margin-top: 5px;
}
</style>
