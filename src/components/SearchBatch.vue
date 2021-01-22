<template>
  <div class="sm:container mx-auto text-center">
    <div class="mt-10 relative rounded-md shadow-sm center">
      <input
        type="text"
        name="batchNumber"
        id="batchNumber"
        class="focus:ring-indigo-500 focus:border-indigo-500 block w-full pl-7 pr-12 sm:text-sm border-gray-300 rounded-md"
        placeholder="Type batch number"
        v-on:keyup.enter="clicked"
      />
    </div>
  </div>
  <div class="container mx-auto mt-10">
    <BatchResult
      :id="id"
      :mfg_date="mfg_date"
      :expiration_date="expiration_date"
      :product_details="product_details"
      :error="error"
    />
  </div>
</template>

<script setup>
import BatchResult from "./BatchResult.vue";
</script>

<script>
import axios from "axios";

export default {
  data: function () {
    console.log(this.props);
    return {
      id: null,
      mfg_date: null,
      expiration_date: null,
      product_details: null,
      error: null,
    };
  },
  methods: {
    clicked: function (event) {
      const batch_number = event.target.value;
      if (batch_number) {
        axios
          .get("http://localhost:8040/api/v1/product/public/" + batch_number)
          .then((response) => {
            console.log(response);
            this.id = response.data.id;
            this.mfg_date = new Date(response.data.mfg_date);
            this.expiration_date = new Date(response.data.expiration_date);
            this.product_details = response.data.product_details;
            this.error = null;
          })
          .catch((error) => {
            this.error = error;
            this.id = null;
          });
      }
    },
  },
};
</script>

<style scoped>
a {
  color: #42b983;
}
</style>
