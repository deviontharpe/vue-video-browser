<template>
  <div class="container">
    <SearchBar v-on:termChange="onTermChange"></SearchBar>
    <VideoList v-bind:videos="videos"></VideoList>
  </div>
</template>

<script>
import axios from "axios";
import SearchBar from "./components/SearchBar";
import VideoList from "./components/VideoList";
const API_KEY = "AIzaSyCf0lHwZmyPHYQaAbi1WSLS4E3QLvVr0yg";

export default {
  name: "App",
  components: {
    SearchBar,
    VideoList
  },
  data() {
    return { videos: [] };
  },
  methods: {
    onTermChange(searchTerm) {
      axios
        .get("https://www.googleapis.com/youtube/v3/search", {
          params: {
            key: API_KEY,
            type: "video",
            part: "snippet",
            q: searchTerm
          }
        })
        .then(response => {
          this.videos = response.data.items;
        });
    }
  }
};
</script>