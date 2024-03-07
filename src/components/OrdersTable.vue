<template>
  <div class="table-container card">
    <thead>
      <tr>
        <th scope="col">SKU</th>
        <th scope="col">Name</th>
        <th scope="col">Quantity</th>
        <th scope="col">Price</th>
      </tr>
    </thead>
    <tbody>
      <tr v-for="(item, index) in getItemDetails" :key="index">
        <td>{{ item.sku || '-' }}</td>
        <td>{{ item.name }}</td>
        <td>{{ item.quantity }}</td>
        <td>{{ item.price }}</td>
      </tr>
    </tbody>
    <div class="box">
      <a class="button" href="#popup1">Buy Products</a>
    </div>

    <div id="popup1" class="overlay">
      <div class="popup">
        <h2>Congrats!</h2>
        <a class="close" href="#">&times;</a>
        <div class="content">You just bought {{ getItemDetails.length }} products</div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  props: {
    orders: Array
  },
  computed: {
    getItemDetails() {
      if (!this.orders) {
        return;
      }
      return this.orders;
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
.table-container {
  border: 2px solid gray;
  padding: 10px;
  margin-top: 10px;
}

.box {
  width: 40%;
  margin: 0 auto;
  padding: 8px;
  border-radius: 20px/50px;
  text-align: center;
}

.button {
  padding: 6px;
  border-radius: 8px;
  border: gray;
  color: black;
  background-color: #e0e0e0;
  text-decoration: none;
  cursor: pointer;
  transition: all 0.3s ease-out;
}
.button:hover {
  background: gray;
  color: beige;
}

.overlay {
  position: fixed;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  background: rgba(0, 0, 0, 0.7);
  transition: opacity 500ms;
  visibility: hidden;
  opacity: 0;
}
.overlay:target {
  visibility: visible;
  opacity: 1;
}

.popup {
  margin: 200px auto;
  padding: 20px;
  background: #fff;
  border-radius: 5px;
  width: 30%;
  position: relative;
  transition: all 5s ease-in-out;
}

.popup h2 {
  margin-top: 0;
  color: #333;
}
.popup .close {
  position: absolute;
  top: 20px;
  right: 30px;
  transition: all 200ms;
  font-size: 24px;
  font-weight: bold;
  text-decoration: none;
  color: #333;
}
.popup .close:hover {
  color: black;
}
.popup .content {
  max-height: 30%;
  overflow: auto;
}
a {
  font-size: 12px;
  font-weight: 500;
}
</style>
