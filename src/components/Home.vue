<!-- eslint-disable vue/multi-word-component-names -->
<template>
  <div>
    <div v-if="loading">Loading orders...</div>
    <div v-else>
      <OrdersOverview :orders="ordersOverview" @orderClicked="orderClicked" />
      <OrderNumber :orderNumber="orderNumber" />
      <div v-if="orderSelected">
        <OrdersTable :orders="orderSelected" />
        <OrdersForm @newOrder="addOrder" />
      </div>
    </div>
  </div>
</template>
<script>
import OrdersForm from '../components/OrdersForm.vue';
import OrdersTable from '../components/OrdersTable.vue';
import OrderNumber from '../components/OrderNumber.vue';
import OrdersOverview from '../components/OrdersOverview.vue';
import axios from 'axios';
export default {
  components: {
    OrdersForm,
    OrdersTable,
    OrderNumber,
    OrdersOverview
  },
  data() {
    return {
      loading: true,
      orders: [],
      ordersItems: [],
      ordersOverview: [],
      orderNumber: null,
      orderSelected: null
    };
  },
  methods: {
    getOrders() {
      const bearer_token = 'eyJhbGciOiJIUzUxMiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJwUGFINU55VXRxTUkzMDZtajdZVHdHV3JIZE81cWxmaCIsImlhdCI6MTYyMDY2Mjk4NjIwM30.lhfzSXW9_TC67SdDKyDbMOYiYsKuSk6bG6XDE1wz2OL4Tq0Og9NbLMhb0LUtmrgzfWiTrqAFfnPldd8QzWvgVQ';
      const config = {
        headers: {
          Authorization: bearer_token
        }
      };
      return axios.get('https://eshop-deve.herokuapp.com/api/v2/orders', config);
    },
    addOrder(order) {
      this.orderSelected.push(order);
    },
    orderClicked(order) {
      this.orderNumber = order.number;
      this.orderSelected = this.orders
        .filter(order => order.number === this.orderNumber)
        .map(order => order.items)
        .flat();
    }
  },
  async created() {
    const fecthedOrders = await this.getOrders();
    this.orders = fecthedOrders.data.orders;
    this.ordersOverview = this.orders;
    this.loading = false;
  }
};
</script>
<style></style>
