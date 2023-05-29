<template>
  <div>
    <img :src="image" width="100" height="100">
    <b-table striped hover :items="albums" :fields="fields"></b-table>
  </div>
</template>

<script>
import axios from "axios";
import image from "./assets/logo.png"

export default {
  data() {
    return {
      albums: [],
      fields: ['album_id', 'title', 'artist', 'genre', 'label', 'songs', 'year'],
      image,
    };
  },
  mounted() {
    axios
      .get("https://albums-collection-service.herokuapp.com/albums")
      .then((response) => {
        this.albums = response.data;
      });
  },
};
</script>