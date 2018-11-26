<template>
    <div>
        <h1 class="text-center">Product List</h1>
        <b-table striped hover :items="products"></b-table>
    </div>
</template>

<script>
import axios from "axios";
export default {
  name: "products",
  data() {
    return {
      message: "Project 2",
      products: []
    };
  },
  mounted() {
    var instance = this;
    axios
      .get("https://shielded-spire-43023.herokuapp.com/api/products/")
      .then(function(response) {
        console.log(response);
        instance.products = response.data.data;
      });
  }
};
</script>
