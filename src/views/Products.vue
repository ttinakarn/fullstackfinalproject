<template>
    <div>
        <h1 class="text-center">Product List</h1>
        <b-table striped hover :items="products" :fields="fields" :per-page="pageSize" :current-page="pageIndex"></b-table>
        <b-pagination :total-rows="products.length" :per-page="pageSize" v-model="pageIndex" />
    </div>
</template>

<script>
import axios from "axios";
export default {
  name: "products",
  data() {
    return {
      message: "Project 2",
      products: [],
      pageSize: 10,
      pageIndex: 1,
      fields: [
        {
          key: "id",
          sortable: true
        },
        {
          key: "title",
          sortable: true
        },
        {
          key: "price",
          sortable: true,
          variant: 'danger'
        }
      ]
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
