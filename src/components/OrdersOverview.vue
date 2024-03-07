<template>
  <div>
    <h3>Orders History</h3>
    <ul class="overview-container card">
      <li v-for="(item, index) in orders" :key="index">Order #: {{ item.number }} <button @click="itemClicked(item)">Details</button></li>
    </ul>
  </div>
</template>
<script>
export default {
  props: {
    orders: Array
  },
  methods: {
    itemClicked(item) {
      this.$emit('orderClicked', item);
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
.overview-container {
  border: 2px solid gray;
  padding: 10px;
  width: 350px;
}
li {
  margin-top: 10px;
  text-decoration: none;
  list-style-type: none;
}
button {
  padding: 6px;
  border-radius: 8px;
  border: gray;
  color: black;
}
button:hover {
  background: gray;
  color: beige;
}
</style>
