<template>
  <div class="container posts-edit">
    <form v-on:submit.prevent="updatePlace()">
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
  data: function() {
    return {
      place: {},
      errors: [],
    };
  },
  created: function() {
    axios.get("/api/places/" + this.$route.params.id).then(response => {
      console.log(response);
      this.place = response.daa;
    });
  },
  methods: {
    updatePlace: function(place) {
      var params = {
        name: post.name,
        address: post.address,
      };
      axios
        .patch("/api/places/" + post.id, params)
        .then(response => { 
          console.log("post updated", response);
          this.$router.push("/places");
        });
    },
  },
};
</script>