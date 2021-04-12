<template>
  <div class="container places-new">
    <form v-on:submit.prevent="createPlace()">
      <h1>New Place</h1>
      <ul>
        <li class="text-danger" v-for="error in errors" v-bind:key="error">
          {{ error }}
        </li>
      </ul>
      <div class="form-group">
        <label>Name:</label>
        <input type="text" class="form-control" v-model="name" />
      </div>
      <div class="form-group">
        <label>Address:</label>
        <input type="text" class="form-control" v-model="address" />
      </div>
      <input type="submit" class="btn btn-primary" value="Submit" />
    </form>
  </div>
</template>


<script>
import axios from "axios";
export default {
  data: function () {
    return {
      name: "",
      address: "",
      errors: [],
    };
  },
  created: function () {},
  methods: {
    createPlace: function () {
      console.log("Creating a Place!");
      var params = {
        name: this.name,
        address: this.address,
      };
      axios
        .post("/api/places", params)
        .then(() => {
          this.$router.push("/places");
        })
        .catch((error) => console.log(error.response));
    },
  },
};
</script>
