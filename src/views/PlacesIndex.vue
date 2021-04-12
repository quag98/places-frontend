<template>
  <div class="home">
    <div>
      <div v-for="place in places" v-bind:key="place.id">
        <h3>{{ place.name }}</h3>
        <p>{{ place.address }}</p>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data: function () {
    return {
      places: [],
    };
  },
  created: function () {
    this.indexPosts();
  },
  methods: {
    indexPlaces: function () {
      axios.get("/api/places").then((response) => {
        this.places = response.data;
        console.log("all places:", this.places);
      });
    },
  },
};
</script>